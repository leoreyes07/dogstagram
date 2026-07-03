<script>
    import { onMount } from "svelte";
    import Header from "../components/Header.svelte";
    import Main from "../components/Main.svelte";
    import TimeLine from "../components/TimeLine.svelte";
    import RightPanel from "../components/RightPanel.svelte";
    import Navigation from "../components/Navigation.svelte";

    let isDarkMode = false;

    onMount(() => {
        // Chequear preferencia del sistema
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            isDarkMode = true;
            document.body.classList.add('dark-mode');
        }
    });

    function toggleTheme() {
        isDarkMode = !isDarkMode;
        if (isDarkMode) {
            document.body.classList.add('dark-mode');
        } else {
            document.body.classList.remove('dark-mode');
        }
    }
</script>

<div class="app-layout">
    <Navigation {isDarkMode} on:toggle={toggleTheme} />
    <div class="main-content">
        <Header />
        <Main>
            <TimeLine />
            <RightPanel />
        </Main>
    </div>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

    :global(:root) {
        /* Light Theme Variables */
        --bg-color: #fafafa;
        --text-color: #000000;
        --text-secondary: #737373;
        --border-color: #dbdbdb;
        --card-bg: #ffffff;
        --nav-bg: #ffffff;
        --link-color: #0095f6;
        --highlight: #efefef;
    }

    :global(body.dark-mode) {
        /* Dark Theme Variables */
        --bg-color: #000000;
        --text-color: #f5f5f5;
        --text-secondary: #a8a8a8;
        --border-color: #262626;
        --card-bg: #000000;
        --nav-bg: #000000;
        --link-color: #e0f1ff;
        --highlight: #1a1a1a;
    }

    :global(body) {
        background-color: var(--bg-color);
        color: var(--text-color);
        font-family: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        margin: 0;
        padding: 0;
        transition: background-color 0.3s ease, color 0.3s ease;
    }

    :global(h1, h2, h3, p) {
        margin: 0;
        padding: 0;
    }

    :global(a) {
        text-decoration: none;
        color: var(--text-color);
    }

    .app-layout {
        display: flex;
        min-height: 100vh;
    }

    .main-content {
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        margin-left: 244px; /* Default sidebar width */
    }

    @media (max-width: 768px) {
        .main-content {
            margin-left: 0;
            margin-bottom: 50px; /* Space for bottom nav */
        }
    }
</style>