<script>
    import {page} from '$app/stores'
    // const boardCode = $page.params['boardCode'];

  const boardCode =  $page.params['boardCode']


    const boardNames = {

        notice: '공지사항' ,
        free1: '잡담' ,
        free2: '방명록'
    };

    const boardName = (boardNames[boardCode] || '') + ' 게시판'.trim();
</script>


<h1>{boardName}</h1>