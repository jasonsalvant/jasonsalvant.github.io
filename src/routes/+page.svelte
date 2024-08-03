<header class={`header1 ${activeClass}`}>
    <a href="/" style="font-family:'Times New Roman', Times, serif">// jasonsalvant //</a>
    <nav>
        <ul>
            <li><a href="/">about</a></li>
            <li><a href="/">selected works</a></li>
            <li><a href="/">explore</a></li>
            <li><a href="/">contact</a></li>
        </ul>
    </nav>
</header>
<div class={`info-marquee ${activeClass}`}>
    <div class='marquee-content'>
        <p><span id='datetime'> New York, NY</span></p>
        <p><span id='temperature'>TEMPERATURE placeholder.</span></p>
        <p><a href="/">ooh! click me! click me!</a></p>
        <p><span>MOON BULLSHIT placeholder.</span></p>
    </div>
</div>
<div class="maincontainer">
    <div class="dropdown-container" class:active={dropdownActive}>
        <span>jason salvant is</span>
        <button class="btn" on:click={toggleDropdown}>...</button>
        {#if dropdownActive}
        <div class="dropdown-content">
            <ul>
                <li><button class="btn dropdown" on:click={() => toggleStyle('writer')}>a writer.</button></li>
                <li><button class="btn dropdown" on:click={() => toggleStyle('editor')}>an editor.</button></li>
                <li><button class="btn dropdown">a heretic.</button></li>
                <li><button class="btn dropdown">a child of god.</button></li>
                <li><button class="btn dropdown">a gemini moon.</button></li>
                <li><button class="btn dropdown">a lover.</button></li>
                <li><button class="btn dropdown">the queen of england.</button></li>
            </ul>
        </div>
        {/if}
    </div>
</div>

<style lang='scss'>
    .header1 {
        position: relative;
        left: 0px;
        right: 0px;
        padding: 10px 20px;
        height: fit-content;
        display: flex; 
        align-items: center;
    }

    .header1 nav ul {
        text-align: center;
        display: flex; 
        list-style-type: none;
        margin: 0;
        padding: 0;
    }

    .header1 nav ul li {
        margin-inline: 10px 10px; /* adds space to the right of list items */
    }

    .info-marquee {
        position: relative;
        left: 0px;
        right: 0px;
        border: 1px solid white;
        padding: 5px 20px;
        margin-bottom: 10px;
        height: fit-content;
    }

    .marquee-content {   
        display: flex; 
        justify-content: space-between;
    }

    .maincontainer {
        display: flex;
        flex-flow: row;
        font-size: 4rem;
        padding: 0px 5px;
        justify-content: center;
    }

    .dropdown-container {
        position: absolute;
    }

    .btn {
        background: white;
        border: none;
        text-decoration: none;
        color: black;
        font-family: inherit;
        font-size: inherit;
        text-align: left;
        cursor: help;
        
    }

    .btn.dropdown {
        background: none;
        color: white;
        left: 0;
        white-space: nowrap;
        padding: 1px 0px;
    }

    .btn.dropdown:hover, .btn.dropdown:focus {
        background: white;
        color: black;
        cursor: pointer;
    }

    .dropdown-content {
        position: absolute;
        z-index: 1;
        pointer-events: auto;
    }

    .dropdown-content ul {
        margin: 0;
        padding: 0;
        list-style-type: none;
    }

    .dropdown-container.active .dropdown-content {
        pointer-events: auto;
        display: block;
    }

    /* custom styles for each class */
    .header1.writer {
        background-color: #f5f5f5;
    }

    .info-marquee.editor {
        background-color: aqua;
    }
</style>

<script lang='ts'>
    import { onMount } from 'svelte';

    let dropdownActive = false;
    let activeClass = '';

    function toggleDropdown() {
        dropdownActive = !dropdownActive;
    }

    function handleClickOutside(e) {
        if (!e.target.closest(".dropdown-container")) {
            dropdownActive = false
        }
    }

    function toggleStyle(className) {
        if (activeClass === className) {
            activeClass = '';
        } else {
            activeClass = className;
        }  
    }

    onMount(() => {
        document.addEventListener('click', handleClickOutside);
        return () => document.removeEventListener('click', handleClickOutside);
    });
</script>
