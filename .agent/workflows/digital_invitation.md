---
description: Create a premium, single-page digital invitation with background music, RSVP, and animations.
---

1. Create the project directory structure.
   ```bash
   mkdir -p assets
   ```

2. Create the main `index.html` with the full feature set (SPA, Music, Loading Screen, RSVP).
   <REPLACE_WITH_TEMPLATE_BELOW>

3. Create a placeholder `task.md` to track customization.
   ```markdown
   # Invitation Customization Task List
   - [ ] Upload background image to `assets/invitation-bg.jpg`
   - [ ] Upload RSVP background to `assets/rsvp-party.jpg`
   - [ ] Upload music file to `assets/music.mp3`
   - [ ] Update `index.html` with event details (Name, Date, Location)
   - [ ] Update `index.html` with Google Forms/FormSubmit link
   ```

4. Notify the user to upload their assets.
   "Project scaffolded! Please upload your images and music to the `assets/` folder and update the event details in `index.html`."

---

# Template for index.html (Paste this in Step 2)

```html
<!DOCTYPE html>
<html class="dark" lang="en">
<head>
    <meta charset="utf-8" />
    <meta content="width=device-width, initial-scale=1.0" name="viewport" />
    <title>Event Invitation</title>
    <script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
    <link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1" rel="stylesheet" />
    <link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,200..800;1,6..72,200..800&display=swap" rel="stylesheet" />
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: "class",
            theme: {
                extend: {
                    colors: {
                        "primary": "#8c25f4",
                        "background-dark": "#191022",
                        "royal-cream": "#FDF5E6",
                        "amethyst": "#473b54",
                    },
                    fontFamily: {
                        "display": ["Newsreader", "serif"],
                        "script": ["Great Vibes", "cursive"],
                    }
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        .watercolor-bg {
            background: radial-gradient(circle at top left, #2e1a47 0%, #191022 100%);
        }
        .placeholder-invisible { visibility: hidden; }
    </style>
</head>
<body class="bg-background-dark text-royal-cream min-h-screen font-display overflow-x-hidden">
    
    <!-- Loading Screen -->
    <div id="loading-screen" class="fixed inset-0 z-[100] bg-[#191022] flex flex-col items-center justify-center transition-opacity duration-1000">
        <h1 class="text-royal-cream text-4xl font-script animate-pulse">Loading...</h1>
    </div>

    <!-- Main App Container -->
    <div id="app-container" class="relative min-h-screen w-full max-w-[480px] mx-auto flex flex-col shadow-2xl bg-[#191022] opacity-0 transition-opacity duration-1000">
        
        <!-- View 1: Invitation -->
        <div id="view-invitation" class="flex-1 flex flex-col relative watercolor-bg">
            <!-- Header -->
            <div class="flex items-center p-4 justify-center z-10 w-full">
                <h2 class="text-royal-cream/70 text-sm font-medium tracking-widest uppercase">Invitation</h2>
            </div>

            <!-- Content -->
            <div class="flex-1 flex flex-col items-center justify-center px-6 text-center py-8">
                <div class="space-y-4 mb-8">
                    <p class="text-primary font-medium tracking-widest uppercase text-xs">You are invited to</p>
                    <h1 class="text-royal-cream text-5xl font-script drop-shadow-lg">Event Name</h1>
                </div>
                
                <div class="mt-4 space-y-6 max-w-xs w-full backdrop-blur-sm bg-white/5 p-6 rounded-2xl border border-white/5 shadow-xl">
                    <div class="flex flex-col items-center gap-1">
                        <span class="material-symbols-outlined text-primary/80 mb-1 text-3xl">calendar_today</span>
                        <h2 class="text-royal-cream text-xl font-semibold">Date Goes Here</h2>
                        <a href="#" class="text-primary text-xs hover:underline mt-1">Add to Calendar</a>
                    </div>
                </div>
            </div>

            <!-- Footer -->
            <div class="p-8 pb-12 flex flex-col items-center z-10 w-full">
                <button onclick="switchView('rsvp')" class="w-full max-w-sm bg-primary hover:bg-primary/90 text-white font-bold py-4 px-8 rounded-full shadow-lg transition-all transform active:scale-95 flex items-center justify-center gap-2">
                    <span class="material-symbols-outlined">mail</span>
                    <span>RSVP Now</span>
                </button>
            </div>
            <div class="h-16"></div>
        </div>

        <!-- View 2: RSVP -->
        <div id="view-rsvp" class="hidden flex-1 flex-col relative watercolor-bg">
            <div class="flex items-center p-6 pb-4 justify-between sticky top-0 z-10 bg-[#191022]/80 backdrop-blur-md">
                <button onclick="switchView('invitation')" class="text-royal-cream flex size-10 items-center justify-center rounded-full hover:bg-white/10">
                    <span class="material-symbols-outlined">chevron_left</span>
                </button>
                <h1 class="text-royal-cream text-xl font-bold flex-1 text-center pr-10">RSVP</h1>
            </div>

            <form id="rsvp-form" class="flex flex-col gap-8 px-6 py-4 pb-12">
                <!-- Add Form Fields Here -->
                <button type="submit" class="w-full bg-primary hover:bg-primary/90 text-white font-bold py-5 px-6 rounded-2xl shadow-lg">Submit RSVP</button>
            </form>
            <div class="h-16"></div>
        </div>
        
        <!-- Music Button -->
        <div class="sticky bottom-6 w-full flex justify-end px-6 pointer-events-none">
            <button id="music-toggle" class="pointer-events-auto bg-white/10 backdrop-blur-md border border-white/20 text-royal-cream p-3 rounded-full shadow-lg hover:bg-white/20 transition-all animate-pulse">
                <span class="material-symbols-outlined" id="music-icon">music_note</span>
            </button>
        </div>
    </div>

    <audio id="bg-music" loop>
        <source src="assets/music.mp3" type="audio/mpeg">
    </audio>

    <script>
        // Copy the SPA logic, Music Logic, and Loading Screen logic from the previous project here.
        // (Simplified for brevity in this template, strictly use the full code in real implementation)
        
        window.addEventListener('load', () => {
            const loader = document.getElementById('loading-screen');
            const app = document.getElementById('app-container');
            setTimeout(() => {
                loader.style.opacity = '0';
                app.style.opacity = '1';
                setTimeout(() => loader.style.display = 'none', 1000);
            }, 1000);
        });

        function switchView(viewName) {
            const inv = document.getElementById('view-invitation');
            const rsvp = document.getElementById('view-rsvp');
            if(viewName === 'rsvp') { inv.classList.add('hidden'); rsvp.classList.remove('hidden'); rsvp.classList.add('flex'); }
            else { rsvp.classList.add('hidden'); inv.classList.remove('hidden'); inv.classList.add('flex'); }
        }
        
        // Add Media Player Logic...
    </script>
</body>
</html>
```
