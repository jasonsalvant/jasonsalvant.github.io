<header class='header1'>
    <a href="/">jasonsalvant dot com</a>
    <nav>
        <ul>
            <li><a href="/">/about</a></li>
            <li><a href="/">/selected works</a></li>
            <li><a href="/">/explore</a></li>
            <li><a href="/">/contact</a></li>
        </ul>
    </nav>
</header>
<div class="info-marquee">
    <div class='marquee-content'>
        <p><span id='datetime'>{currentDateTime}, New York, NY</span></p>
        <p><span id='temperature'>TEMPERATURE placeholder.</span></p>
        <p><a href="/">ooh! click me! click me!</a></p>
        <p><span>MOON BULLSHIT placeholder.</span></p>
    </div>
</div>
<div class='maincontainer'>
    <div class='dropdown-container'>
        <p>jason salvant is <span class='dropdown'>a writer.
            <div class='dropdown-content'>
                <p class='dropdown-item'>an editor.</p>
                <p class='dropdown-item'>a heretic.</p>
                <p >a screenwriter.</p>
                <p>a musician.</p>
                <p>a DJ.</p>
                <p>a fag.</p>
                <p>a cutie.</p>
                <p>a child of god</p>
                <p>a child of dog</p>
                <p>a lovecraftian horror.</p>
                <p>a patron of the arts.</p>
                <p>an aspiring philosopher king.</p>
                <p>a fucking uhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh.</p>
            </div>
        </span></p>
    </div>
    <img src="testimage.jpg" alt="me" height="30%" width="30%">
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
    }

    .dropdown-container {
        position: absolute;
        font-size: 4em;
        padding: 0px 5px;
    }

    .dropdown {
        position: relative;
        display: inline-block;
        color: aqua;
    }

    .dropdown-content {
        display: none;
        white-space: nowrap;
        overflow: hidden;
        position: absolute;
        z-index: 1;
    }

    .dropdown:hover .dropdown-content {
        display: block;
    }
</style>

<script lang="ts">
    import { onMount } from 'svelte';

    let currentDateTime: string | undefined;

    onMount(() => {
        function updateDateTime() {
            const now = new Date();
            currentDateTime = now.toLocaleString();
        }

        updateDateTime();
        const interval = setInterval(updateDateTime, 1000);

        return () => clearInterval(interval);
    });
</script>