<script>
    // GitHub 사용자 이름을 설정
    let username = $state('');
    // 리포지토리 목록을 저장할 상태
    let repositories = $state([]);
    // 컴포넌트 마운트 시 GitHub API로부터 데이터 가져오기
   async function fetchRepositories() {
        const response = await fetch(`https://api.github.com/users/${username}/repos?per_page=30`);
        repositories = await response.json();
   }
</script>

<svelte:head>
    <title>{username}'s repositories</title>
    <meta name="description" content="레포지터리 목록 가져오기"/>
</svelte:head>



<div class="p-5">

    <form on:submit|preventDefault = {fetchRepositories} >

        <input type = "text" bind:value={username} placeholder = "깃허브 사용자 이름을 입력 하세요." size="30"/>
        <button type="submit">레포지터리 목록 가져오기</button>
    </form>

    {#if username}

        <h1>{username}'s repositories</h1>

        <ul>
            {#each repositories as repo} <!--반복문-->
                <li>
                    {repo.name}
                </li> <!-- 여기서 repo 객체의 다른 속성도 사용할 수 있습니다 -->
            {/each}
        </ul>
        {/if}
        </div>



