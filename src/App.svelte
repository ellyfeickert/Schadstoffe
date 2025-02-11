<script>
    let hoveredSubstance = null;

    let substances = [
        { 
            name: "Schwefeldioxid SO₂", 
            description: `
                <b>Schwefeldioxid (SO₂)</b> ist ein giftiges Gas, das bei der Verbrennung fossiler Brennstoffe wie Kohle und Erdöl entsteht.<br><br>
                Da Schiffskraftstoffe einen Schwefelanteil von bis zu <b>0,5%</b> haben können, verursachen diese besonders hohe Schwefeldioxidemissionen.<br><br>
                <b>Schwefeldioxid verursacht in hohen Konzentrationen sauren Regen.</b>
            `,
            area: { top: 65, left: 5, width: 30, height: 30 }  
        },
        { 
            name: "Stickoxide NOx", 
            description: `
                <b>Stickoxide</b> sind gasförmige Verbindungen aus Stickstoff (N) und Sauerstoff (O).<br><br>
                Sie entstehen als Nebenprodukte bei Verbrennungsprozessen. Hauptquellen sind Verbrennungsmotoren, sowie Verbrennung von Kohle, Gas, Holz und Abfällen.<br><br>
                <b>Stickoxide gelten als Vorläuferstoffe zur Bildung von Ozon und Feinstaub.</b>
            `,
            area: { top: 35, left: 38, width: 25, height: 25 }  
        },
        { 
            name: "Feinstaub", 
            description: `
                <b>Feinstaub</b> oder Particulate Matter (PM) sind Teilchen in der Luft, die aufgrund ihrer Größe nicht sofort zu Boden sinken, sondern eine gewisse Zeit in der Atmosphäre verweilen.<br><br>
                Feinstaub wird in zwei Größen unterschieden:<br>
                <b>Feinstaub PM10</b> und <b>Feinstaub PM2,5</b>.<br><br>
                Feinstaub entsteht durch Emissionen aus Kraftfahrtzeugen, Kraft- und Fernheizwerken, Öfen und Heizungen.<br><br>
                <b>Der Straßenverkehr, insbesondere der Reifen- und Bremsantrieb, gilt als primärer Verursacher.</b><br><br>
                Feinstaub kann in hohen Konzentrationen zu Schleimhautreizungen und einer erhöhten Neigung zu Thrombose führen.
            `,
            area: { top: 5, left: 5, width: 30, height: 30 }  
        },
        { 
            name: "Kohlendioxid CO₂", 
            description: `
                <b>Kohlendioxid (CO₂)</b> ist eines der bedeutendsten Treibhausgase: Der Anteil an Kohlendioxid an den Gesamtemissionen betrug <b>88,7 %</b> im Jahr 2023.<br><br>
                <b>Auswirkungen des Klimawandels auf die Erde:</b><br>
                - Extreme Wetterereignisse werden intensiver und häufiger.<br>
                - Der Meeresspiegel steigt an.<br>
                - Globaler Eisverlust und damit einhergehendes Verschwinden des arktischen Lebensraums.
            `,
            area: { top: 10, left: 60, width: 30, height: 30 }  
        }
    ];
</script>

<style>
    .container {
        position: relative;
        display: inline-block;
        width: 100%;
    }
    
    .clickable-area {
        position: absolute;
        cursor: pointer;
        background: rgba(255, 0, 0, 0.0); /* Unsichtbar, aber hover-aktiv */
    }

    .info-box {
        position: absolute;
        background: rgba(255, 255, 255, 0.85);
        color: #427fb7;
        padding: 20px;
        border-radius: 8px;
        z-index: 10;
        font-family: 'ST Serif';
        font-size: 18px;
        text-align: justify;
        width: 400px; /* Einheitliche Breite */
        max-width: 400px;
        box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
    }
</style>

<div class="container">
    <img src="/data/Schadstoffe.jpg" alt="Harmful substances" style="width:100%; position:relative;">
    
    {#each substances as substance}
        <div 
            class="clickable-area"
            style="top: {substance.area.top - 5}%; left: {substance.area.left - 5}%; width: {substance.area.width + 10}%; height: {substance.area.height + 10}%;"
            on:mouseover={() => hoveredSubstance = substance}
            on:mouseleave={() => hoveredSubstance = null}>
        </div>

        {#if hoveredSubstance === substance}
            <div class="info-box" 
                style="
                    top: {substance.name === 'Schwefeldioxid SO₂' 
                        ? substance.area.top 
                        : (substance.area.top + substance.area.height + 3)}%;
                    left: {substance.name === 'Schwefeldioxid SO₂' 
                        ? (substance.area.left + substance.area.width + 3) 
                        : substance.area.left}%;
                ">
                <p>{@html substance.description}</p>
            </div>
        {/if}
    {/each}
</div>
