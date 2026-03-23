---
layout: post
codemirror: true
title: My Game Levels Review
permalink: /game-engine/individual
---

## Level 1 Reflection

Paragraph 1 :  
Game Runner for Level 1:  

When I started creating Level 1 of my game, I focused on building a strong foundation using the game engine structure that connects different components like the background, player, NPCs, and barriers. I imported all the essential classes like GameControl, GameEnvBackground, Player, Npc, and Barrier so I could reuse code instead of rewriting everything. I created a class called GameLevelChetslime and used the gameEnv path to correctly load images so it works both locally and on GitHub Pages. I designed the alien planet background and adjusted pixel sizes so it scales properly. Then I set up the player with movement speed, animations, and WASD controls so it feels smooth. I added directional animations to make movement look realistic. I also created an NPC named Bob Miller with dialogue to guide the player and placed a barrier to block parts of the map. I had to debug issues like module import errors and fixed them by switching to absolute paths. In the end, I combined everything into a classes array so the engine loads everything correctly, making the level fully playable.

## Level 1

{% capture code1 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';
import Npc from '/assets/js/GameEnginev1/essentials/Npc.js';
import Barrier from '/assets/js/GameEnginev1/essentials/Barrier.js';

class GameLevelChetslime {
    constructor(gameEnv) {
        const path = gameEnv.path;

        const bgData = {
            name: "custom_bg",
            src: path + "/images/gamebuilder/bg/alien_planet.jpg",
            pixels: { height: 772, width: 1134 }
        };

        const playerData = {
            id: 'playerData',
            src: path + "/images/gamebuilder/sprites/slime.png",
            SCALE_FACTOR: 5,
            STEP_FACTOR: 1000,
            ANIMATION_RATE: 50,
            INIT_POSITION: { x: 0, y: 453 },
            pixels: { height: 225, width: 225 },
            orientation: { rows: 4, columns: 4 },
            down: { row: 2, start: 0, columns: 3 },
            left: { row: 0, start: 0, columns: 3 },
            right: { row: 1, start: 0, columns: 3 },
            up: { row: 3, start: 0, columns: 3 },
            hitbox: { widthPercentage: 0, heightPercentage: 0 },
            keypress: { up: 87, left: 65, down: 83, right: 68 }
        };

        const npcData1 = {
            id: 'Bob Miller',
            greeting: 'Do NOT go past these mountains!',
            src: path + "/images/gamify/chillguy.png",
            SCALE_FACTOR: 3,
            ANIMATION_RATE: 999999,
            INIT_POSITION: { x: 629, y: 208 },
            pixels: { height: 150, width: 505 },
            orientation: { rows: 1, columns: 3 },
            down: { row: 0, start: 0, columns: 3 },
            hitbox: { widthPercentage: 0.1, heightPercentage: 0.2 },
            dialogues: ['Do NOT go past these mountains!'],
            interact: function() { if (this.dialogueSystem) this.showRandomDialogue(); }
        };

        const barrier = {
            id: 'b1', x: 527, y: 110, width: 49, height: 240, visible: true
        };

        this.classes = [
            { class: GameEnvBackground, data: bgData },
            { class: Player, data: playerData },
            { class: Npc, data: npcData1 },
            { class: Barrier, data: barrier }
        ];
    }
}

export const gameLevelClasses = [GameLevelChetslime];
export { GameControl };
{% endcapture %}

{% include game-runner.html runner_id="level1" code=code1 %}

---

## Level 2 Reflection

Paragraph 2 :  
Game Runner for Level 2:  

For Level 2, I wanted to make the game more interactive, so I added a new mechanic called an aura system. I reused the same engine structure but focused on adding dynamic behavior. I created a global auraScore and displayed it on screen using a fixed div styled with JavaScript. This made the game feel more like a real system with feedback. I wrote an updateAura function that increases the score whenever the player interacts with an NPC. I also made sure the score display doesn’t duplicate by checking if it already exists. I reused the player and background setup but focused more on interaction. The NPC now triggers both dialogue and score updates, making it more meaningful. This level helped me learn how to combine the game engine with DOM manipulation and make gameplay more engaging instead of just movement.

## Level 2

{% capture code2 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';
import Npc from '/assets/js/GameEnginev1/essentials/Npc.js';
import Barrier from '/assets/js/GameEnginev1/essentials/Barrier.js';

class GameLevelChetinteractive {
    constructor(gameEnv) {
        const path = gameEnv.path;

        if (!window.auraScore) {
            window.auraScore = 0;
            const auraDisplay = document.createElement("div");
            auraDisplay.id = "auraScore";
            auraDisplay.innerText = "Aura: 0";
            auraDisplay.style.position = "fixed";
            auraDisplay.style.bottom = "20px";
            auraDisplay.style.left = "50%";
            auraDisplay.style.transform = "translateX(-50%)";
            auraDisplay.style.background = "black";
            auraDisplay.style.color = "white";
            auraDisplay.style.padding = "10px";
            document.body.appendChild(auraDisplay);
        }

        function updateAura() {
            window.auraScore += 5;
            document.getElementById("auraScore").innerText = "Aura: " + window.auraScore;
        }

        const bgData = {
            name: "custom_bg",
            src: path + "/images/gamebuilder/bg/clouds.jpg",
            pixels: { height: 720, width: 1280 }
        };

        const playerData = {
            id: 'playerData',
            src: path + "/images/gamebuilder/sprites/slime.png",
            SCALE_FACTOR: 5,
            STEP_FACTOR: 1000,
            INIT_POSITION: { x: 25, y: 600 },
            pixels: { height: 225, width: 225 },
            orientation: { rows: 4, columns: 4 },
            keypress: { up: 87, left: 65, down: 83, right: 68 }
        };

        const npc = {
            id: 'chill guy',
            greeting: 'Aura Updated',
            src: path + "/images/gamify/chillguy.png",
            SCALE_FACTOR: 4,
            INIT_POSITION: { x: 232, y: 215 },
            pixels: { height: 512, width: 384 },
            orientation: { rows: 4, columns: 3 },
            dialogues: ['Aura Updated'],
            interact: function() {
                if (this.dialogueSystem) this.showRandomDialogue();
                updateAura();
            }
        };

        this.classes = [
            { class: GameEnvBackground, data: bgData },
            { class: Player, data: playerData },
            { class: Npc, data: npc }
        ];
    }
}

export const gameLevelClasses = [GameLevelChetinteractive];
export { GameControl };
{% endcapture %}

{% include game-runner.html runner_id="level2" code=code2 %}

---

## Level 3 Reflection

Paragraph 3 :  
Game Runner for Level 3:  

In Level 3, I focused on customizing assets and making the game feel more unique. I reused the same engine structure but changed the NPC and visuals. I added a custom character called surronster and adjusted scaling and positioning so it displays correctly. I made sure the player system stayed consistent so movement feels the same across all levels. This level was more about refining visuals and making sure assets load correctly, especially on GitHub Pages. I used the gameEnv path carefully so images work both locally and online. This helped me understand asset management and consistency while still making each level feel different.

## Level 3

{% capture code3 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';
import Npc from '/assets/js/GameEnginev1/essentials/Npc.js';
import Barrier from '/assets/js/GameEnginev1/essentials/Barrier.js';

class GameLevelChetcustom {
    constructor(gameEnv) {
        const path = gameEnv.path;

        const bgData = {
            name: "custom_bg",
            src: path + "/images/gamebuilder/bg/clouds.jpg",
            pixels: { height: 720, width: 1280 }
        };

        const playerData = {
            id: 'playerData',
            src: path + "/images/gamebuilder/sprites/slime.png",
            SCALE_FACTOR: 5,
            STEP_FACTOR: 1000,
            INIT_POSITION: { x: 33, y: 587 },
            pixels: { height: 225, width: 225 },
            orientation: { rows: 4, columns: 4 },
            keypress: { up: 87, left: 65, down: 83, right: 68 }
        };

        const npc = {
            id: 'surronster',
            greeting: 'Go to orbitalmoto',
            src: path + "/images/gamebuilder/sprites/surronster.jpg",
            SCALE_FACTOR: 7,
            INIT_POSITION: { x: 500, y: 300 },
            pixels: { height: 1223, width: 1505 },
            orientation: { rows: 1, columns: 3 },
            dialogues: ['Go to orbitalmoto'],
            interact: function() { if (this.dialogueSystem) this.showRandomDialogue(); }
        };

        this.classes = [
            { class: GameEnvBackground, data: bgData },
            { class: Player, data: playerData },
            { class: Npc, data: npc }
        ];
    }
}

export const gameLevelClasses = [GameLevelChetcustom];
export { GameControl };
{% endcapture %}

{% include game-runner.html runner_id="level3" code=code3 %}