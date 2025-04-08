// ==UserScript==
// @name         Kill YouTube Create Button Animation
// @namespace    https://your.stylus-helper.cool
// @version      1.1
// @description  No more blinking +Create button on YouTube
// @author       You
// @match        https://www.youtube.com/*
// @grant        none
// @updateURL    https://raw.githubusercontent.com/Glehnmarc/tampermonkey-scripts/main/Death%20to%20YouTube's%20Flicking%20Create%20Button
// @downloadURL  https://raw.githubusercontent.com/Glehnmarc/tampermonkey-scripts/main/Death%20to%20YouTube's%20Flicking%20Create%20Button
// ==/UserScript==

(function() {
    'use strict';

    function removeAnimationStyles(element) {
        element.style.setProperty('animation', 'none', 'important');
        element.style.setProperty('transition', 'none', 'important');
        element.style.setProperty('opacity', '1', 'important');
    }

    function nukeCreateButton() {
        const createBtn = document.querySelector('ytd-topbar-menu-button-renderer[button-renderer*="create"]');
        if (createBtn) {
            removeAnimationStyles(createBtn);
            createBtn.querySelectorAll('*').forEach(el => {
                removeAnimationStyles(el);
            });
        }
    }

    // Run once immediately
    nukeCreateButton();

    // Keep watching for any changes
    const observer = new MutationObserver(() => {
        nukeCreateButton();
    });

    observer.observe(document.body, {
        childList: true,
        subtree: true
    });

    // Run every 10 seconds just in case YouTube tries sneaky tricks
    setInterval(nukeCreateButton, 10000);
})();

