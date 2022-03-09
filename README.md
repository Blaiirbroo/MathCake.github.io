<!DOCTYPE html>
<html>
<head>
<meta name="description" content="Access the world wide web">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="stylesheet" href="css/index.css">
<link rel="icon" href="" id="favicon">
<script src="./script/particles.js"></script>
<script async>
            // Incognito analytics
            // Only tracks user visits!
            // Remove when needed.
            navigator.sendBeacon('./data/visit');
            (async() => {
                const res = await fetch('./data/create-id');
                const id = await res.text();
    
                setInterval(() => {
                    navigator.sendBeacon('./data/keep-alive', id);
                }, 15000)
    
                window.addEventListener('beforeunload', () => {
                    navigator.sendBeacon('./data/destroy', id);
                });
    
            })();
        </script>
</head>
<body>
<script>
            document.body.setAttribute('data-appearance', (localStorage.getItem('incog||appearance')))
        </script>
<header data-init>
<div class="search"></div>
<nav></nav>
<a id="open-nav"><i style="color: var(--accent)" class="fas fa-sliders-h secondary"></i></a>
<a id="close-nav">close</a>
</header>
<main></main>
<iframe src="about:blank" class="access-frame" style="position: absolute; overflow-x: hidden; width: 100%; height: 100%; display: none; border: none; background: #FFF;"></iframe>
<form id="access-form"></form>
<div class="particles"></div>
<script src="script/index.js" type="module"></script>
</body>
</html>
