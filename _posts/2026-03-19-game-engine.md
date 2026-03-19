---
layout: post
codemirror: true
title: My Game Levels
permalink: /game-engine/chetall
---

## Level 1

{% capture code1 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from './essentials/GameEnvBackground.js';
import Player from './essentials/Player.js';
import Npc from './essentials/Npc.js';
import Barrier from './essentials/Barrier.js';

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

## Level 2

{% capture code2 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from './essentials/GameEnvBackground.js';
import Player from './essentials/Player.js';
import Npc from './essentials/Npc.js';
import Barrier from './essentials/Barrier.js';

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

## Level 3

{% capture code3 %}
import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from './essentials/GameEnvBackground.js';
import Player from './essentials/Player.js';
import Npc from './essentials/Npc.js';
import Barrier from './essentials/Barrier.js';

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