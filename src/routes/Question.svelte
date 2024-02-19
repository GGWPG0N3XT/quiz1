<script>
    import {onMount} from 'svelte';
    export let question;
    export let correct_answer;
    export let incorrect_answers;
    
    
    let possibleAnswers = shuffle([...incorrect_answers,correct_answer]);
    const handleClick = (answer) =>{
        if(answer == correct_answer){
            alert("Tacno!")
        }
        else{
            alert(`Netačno! Tačan odgovor je ${correct_answer}`)
        }
    }
    const getQuestion = async () => {
        const res = await fetch  ('https://opentdb.com/api.php?amount=1&category=14&difficulty=easy&type=multiple')
        let data= await res.json();
        question = data.results[0].question;
        console.log(data);
    }
    onMount(getQuestion);
</script>
    

<div>
    <h3>{@html question}</h3>
    <div id = "answers">
        {#each possibleAnswers as pa}
            <button on:click= {() => handleClick(pa)}>{pa}</button>
        {/each}
    </div>
</div>