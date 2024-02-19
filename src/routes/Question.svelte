<script>
    export let question;
    export let correctAnswer;
    export let incorrectAnswers;
    
    const shuffle = (array) => array.sort( () => .5 - Math.random() );
    let possibleAnswers = shuffle([...incorrectAnswers,correctAnswer]);
    const handleClick = (answer) =>{
        if(answer == correctAnswer){
            alert("Tacno!")
        }
        else{
            alert(`Netačno! Tačan odgovor je ${correctAnswer}`)
        }
    }
</script>

<div>
    <h3>{@html question}</h3>
    <div id = "answers">
        {#each possibleAnswers as pa}
            <button on:click= {() => handleClick(pa)}>{pa}</button>
        {/each}
    </div>
</div>