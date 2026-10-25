Step 1 & 2: HTML Structure & Viewport Meta Tag (index.html)
Create or update your HTML file to include the essential viewport meta tag in the <head> section, ensuring proper scaling on mobile devices.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <!-- Step 2: Crucial viewport meta tag for responsive design -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Photo Gallery</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header class="header">
        <h1>My Photo Gallery</h1>
        <p>A responsive mobile-first showcase</p>
    </header>

    <main class="gallery-container">
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb" alt="Mountain View">
            <div class="caption">Mountain View</div>
        </div>
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05" alt="Misty Forest">
            <div class="caption">Misty Forest</div>
        </div>
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1426604966848-d7adac902bff" alt="Serene River">
            <div class="caption">Serene River</div>
        </div>
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1469474968028-56623f02e42e" alt="Golden Hour">
            <div class="caption">Golden Hour</div>
        </div>
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1501785888041-af3ef285b470" alt="Alpine Lake">
            <div class="caption">Alpine Lake</div>
        </div>
        <div class="gallery-item">
            <img src="https://images.unsplash.com/photo-1447752875215-b2761acb3c5d" alt="Pine Woods">
            <div class="caption">Pine Woods</div>
        </div>
    </main>

    <footer class="footer">
        <p>&copy; 2026 Photo Gallery Project. All rights reserved.</p>
    </footer>
</body>
</html>

Steps 3, 4, 5 & 7: Mobile-First CSS with Breakpoints (style.css)
In this stylesheet:

Mobile-First (Step 3): Base styles target small screens by default (single-column flex layout).

Breakpoints (Steps 4 & 5): Uses two breakpoints (768px for tablets and 1024px for desktops) to scale up the layout using CSS Grid.

Overflow & Layout Fixes (Step 7): Uses box-sizing: border-box, overflow-x: hidden, and fluid image sizing (width: 100%, height: auto) to prevent horizontal scrolling and overlapping elements.

/* ==========================================
   1. MOBILE-FIRST BASE STYLES (< 768px)
   ========================================== */
*, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    line-height: 1.5;
    color: #333;
    background-color: #f8f9fa;
    overflow-x: hidden; /* Step 7: Prevents horizontal scrolling overflow */
}

.header {
    background-color: #1a1a1a;
    color: #ffffff;
    text-align: center;
    padding: 1.5rem 1rem;
}

.header h1 {
    font-size: 1.5rem;
    margin-bottom: 0.25rem;
}

.header p {
    font-size: 0.9rem;
    color: #aaa;
}

/* Single column stack layout for mobile devices */
.gallery-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
    width: 100%;
}

.gallery-item {
    background: #ffffff;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.gallery-item img {
    width: 100%; /* Fluid images prevent overflow */
    height: auto;
    display: block;
    object-fit: cover;
}

.caption {
    padding: 0.75rem 1rem;
    font-size: 0.95rem;
    font-weight: 500;
    text-align: center;
}

.footer {
    text-align: center;
    padding: 1rem;
    font-size: 0.85rem;
    color: #666;
    background-color: #e9ecef;
}

/* ==========================================
   2. BREAKPOINT 1: TABLET (min-width: 768px)
   ========================================== */
@media (min-width: 768px) {
    .header {
        padding: 2rem;
    }

    .header h1 {
        font-size: 2rem;
    }

    /* Switch to a 2-column Grid for Tablets */
    .gallery-container {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 1.5rem;
        padding: 1.5rem;
        max-width: 750px;
        margin: 0 auto;
    }
}

/* ==========================================
   3. BREAKPOINT 2: DESKTOP (min-width: 1024px)
   ========================================== */
@media (min-width: 1024px) {
    .header h1 {
        font-size: 2.5rem;
    }

    /* Switch to a 3-column Grid for Desktops */
    .gallery-container {
        grid-template-columns: repeat(3, 1fr);
        gap: 2rem;
        padding: 2rem;
        max-width: 1100px;
    }
}
Step 6: Testing Instructions
Open your index.html file in the Google Chrome browser.

Press F12 (or right-click anywhere and select Inspect) to open Chrome DevTools.

Click the Toggle Device Toolbar icon (or press Ctrl + Shift + M / Cmd + Shift + M) to enter Device Mode.

Test and verify across different device presets:

Mobile View: Test on iPhone SE or Pixel 5 (Verify single-column stack, legible font sizes, and zero horizontal scroll).

Tablet View: Test on iPad Mini or iPad Air (Verify transition to 2-column grid layout).

Desktop View: Resize window or select Responsive / Desktop (Verify transition to 3-column grid layout).