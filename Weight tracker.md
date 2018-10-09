Weight Tracker is a [[Script API]] showcase present in the [[demo document|Document#demo-document]].

[[Day notes]] shows (among others) how we have "weight" [[promoted attribute|promoted attributes]] in the day note [[template]]. This then aggregates the data and shows a nice chart of weight change in time.

## Demo
[[images/weight-tracker.png]]

## Implementation

Note "Weight Tracker" in the screenshot above is of type "Render HTML note". Such note doesn't have any useful content itself, the only purpose of it is to provide a place where some [[script|scripts]] can render some output. This script is defined in [[relation|attributes]] `renderNote` - coincidentally it's the Weight Tracker's child `Implementation`.

This Implementation [[code note|code notes]] then contains some HTML and JavaScript which loads all the notes with "weight" attribute and displays them in a chart. To actually render chart we're using third party library [chart.js](https://www.chartjs.org/) which is imported as an attachment (it's not built-in into Trilium).

### JS code
To get an idea of the script, here's the "JS code" note content:

```javascript
async function getChartData() {
    const days = await api.runOnServer(async () => {
        const notes = await api.getNotesWithLabel('weight');
        const days = [];

        for (const note of notes) {
            const date = await note.getLabelValue('dateNote');
            const weight = parseFloat(await note.getLabelValue('weight'));

            if (date && weight) {
                days.push({ date, weight });
            }
        }

        days.sort((a, b) => a.date > b.date ? 1 : -1);

        return days;
    });

    const datasets = [
        {
            label: "Weight (kg)",
            backgroundColor: 'red',
            borderColor: 'red',
            data: days.map(day => day.weight),
            fill: false,
            spanGaps: true,
            datalabels: {
                display: false
            }
        }
    ];

    return {
        datasets: datasets,
        labels: days.map(day => day.date)
    };
}

const ctx = $("#canvas")[0].getContext("2d");

new chartjs.Chart(ctx, {
    type: 'line',
    data: await getChartData()
});
```