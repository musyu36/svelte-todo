<script>
    // 先頭が$のものはSvelteの組み込み　libは例外
    import {goto} from '$app/navigation'
    import * as api from '$lib/api_client.ts'

    // プロパティ宣言
    export let todo = "";

    // TODOを新規登録する
    async function submit(){
        await api.post('/api/todo', {todo});
        goto('/');
    }
</script>

<h1>TODO追加</h1>

<form on:submit|preventDefault={submit}>
    <!-- bind:valueで入力値をプロパティーにバインドさせることで、スクリプト側で値を取得 -->
    <input type="text" placeholder="TODO" bind:value={todo}>
    <br>
    <button>追加</button>
</form>