<script>
    import { Heading, P } from 'flowbite-svelte';

    const privateSchedule = [
        {
            lesson: "Student Pilot Regulations",
            tasks: ["Documents", "Privileges and Limitations", "Endorsements"],
        },
        {
            lesson: "Aircraft",
            tasks: ["Documents", "Required Inspections"],
        },
        {
            lesson: "Preflight Procedures",
            tasks: ["Preflight Inspection", "Checklist Usage - Types", "CRM/SRM", "Amplified Checklist", "Passenger Briefing"],
        },
        {
            lesson: "Flight Controls",
            tasks: ["Primary Flight Controls", "Secondary Flight Controls"],
        },
        {
            lesson: "Powerplant",
            tasks: ["Engine", "Oil System", "Engine Failures"],
        },
        {
            lesson: "Ignition System",
            tasks: ["Ignition System Overview", "Magnetos", "Spark Plugs"],
        },
        {
            lesson: "Fuel System",
            tasks: ["Fuel System Overview", "Fuel Injection", "Fuel Types", "Emergency Management"],
        },
        {
            lesson: "Electrical System",
            tasks: ["Electrical System Overview", "Starter", "Alternator", "Emergency Management"],
        },
        {
            lesson: "Radio Communications",
            tasks: ["Procedures", "Loss of Communication", "Light Gun Signals"],
        },
        {
            lesson: "Taxi Procedures",
            tasks: ["Overview of Proper Procedures", "Crosswind Taxi Procedures"],
        },
        {
            lesson: "Runway Incursion Avoidance",
            tasks: ["Cockpit Management", "Pilot Deviations"],
        },
        {
            lesson: "Collision Avoidance",
            tasks: ["Traffic Scanning Techniques", "See-and-Avoid"],
        },
        {
            lesson: "Aerodynamics",
            tasks: ["Production of Lift", "Turns"],
        },
        {
            lesson: "Aerodynamics",
            tasks: ["Stalls", "Loss of Control"],
        },
        {
            lesson: "Aerodynamics",
            tasks: ["Production of Drag", "Wake Turbulence"],
        },
        {
            lesson: "Aerodymaics",
            tasks: ["Production of Thrust", "Left Turning Tendencies", "Climb Aerodynamics"],
        },
        {
            lesson: "Stalls and Spins (Deep Dive)",
            tasks: ["In depth analysis and understanding of stalls and spins"],
        },
        {
            lesson: "Aircraft Stability",
            tasks: ["Weight and Balance"],
        },
        {
            lesson: "Performance and Limitations",
            tasks: ["Pressure Altitude", "Density Altitude"],
        },
        {
            lesson: "Performance and Limitations",
            tasks: ["Performance Charts"],
        },
        {
            lesson: "Traffic Patterns",
            tasks: ["Approaches", "Go Arounds"],
        },
        {
            lesson: "Airspace",
            tasks: ["Class A, B, C, D, E", "Special Use Airspace"],
        },
        {
            lesson: "Weather Theory",
            tasks: ["Part 1 of 2"],
        },
        {
            lesson: "Weather Theory",
            tasks: ["Part 2 of 2"],
        },
        {
            lesson: "Weather Products",
            tasks: ["Weather Reports", "Weather Forecasts"],
        },
        {
            lesson: "Cross-country Flight Planning",
            tasks: ["Route Planning", "Navigation Logs", "Pilotage", "Dead Reckoning"],
        },
        {
            lesson: "Human Factors Part 1",
            tasks: ["Obtaining Medical Certificates", "Medical Certificates", "Hypoxia"],
        },
        {
            lesson: "Human Factors Part 2",
            tasks: ["Inner Ear", "Supplemental Oxygen Requirements"],
        },
        {
            lesson: "Night Operations",
            tasks: ["Night Vision", "Night Taxi", "Optical Illusions"],
        },
        {
            lesson: "Private Pilot Privileges and Limitations",
            tasks: ["Expense Sharing", "Compensation"],
        },
    ];

    /* DEFINING ARRAY OF NEXT PILOT CLASSES
        [
            {
                LESSONOBJECT
                DATE
            }
        ]
    */

    let privateClasses = [];
    let privateClassDays = [0,1,2,3,4,5,6]; //0 indicates sunday etc
    let privateClassTimes = [
        "14:00 - 16:00",
        "12:00 - 14:00",
        "14:00 - 16:00",
        "14:00 - 16:00",
        "14:00 - 16:00",
        "14:00 - 16:00",
        "12:00 - 14:00",
    ];
    function nextPrivateClasses() {
        let currentDate = new Date();
        let startDate = new Date(2025, 9, 1);
        console.log("start date: " + startDate);
        let classIndex = 0;

        while (currentDate.getDate() > startDate.getDate()) {
            if (privateClassDays.includes(startDate.getDay())) {
                classIndex++;
                startDate.setDate(startDate.getDate() + 1);
            }
        }
        
        while (privateClasses.length < 3) {
            if (privateClassDays.includes(startDate.getDay())) {
                privateClasses.push({
                    lesson: privateSchedule[classIndex % privateSchedule.length],
                    date: new Date(startDate),
                    dayIndex: startDate.getDay(),
                });
                classIndex++;
            }
            console.log(startDate);
            console.log(privateClasses);
            startDate.setDate(startDate.getDate() + 1);
        }

        console.log(privateClasses);
        
    }

    nextPrivateClasses();
</script>

<div class="container">
    <h1 class="title">GROUND SCHOOL</h1>
    <div class="classGrid">
        <div class="girdItem">
            <h2>Private Pilot</h2>
            {#each privateClasses as privateClass}
                <h3>{privateClass.date.toLocaleDateString("en-US",{weekday: "long", month: "long", day: "numeric"})} | {privateClassTimes[privateClass.dayIndex]}</h3>
                <h3>{privateClass.lesson.lesson}</h3>
                <ul>
                    {#each privateClass.lesson.tasks as task}
                        <li>{task}</li>
                    {/each}
                </ul>
                <div class="spacer"></div>
            {/each}
        </div>
        <div class="gridItem">
            <h2>Instrument</h2>
            <div class="blank"></div>
        </div>
        <div class="gridItem">
            <h2>Commercial</h2>
            <div class="blank"></div>
        </div>
    </div>
</div>


<style>
    :global(.blank) {
        width: 300px;
    }
    :global(.spacer) {
        height: 10px;
    }
    :global(li) {
        list-style-type: disc;
        margin-left: 20px;
    }
    :global(.classGrid) {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
    }
    :global(h3) {
        font-weight: bold;
    }
    :global(h2) {
        color: #39488e;
        font-weight: bold;
        font-size: 2rem;
    }
    :global(h1) {
        color: #39488e;
        font-weight: bold;
        font-size: 4rem;
    }
    :global(.container) {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        min-width: 100vw; /* Full width of the viewport */
        height: 100vh; /* Full height of the viewport */
        margin: 0;
        padding: 0;
        
    }
    :global(html, body) {
        margin: 0;
        padding: 0;
        width: 100%;
        height: 100%;
        overflow-x: hidden;
    }
    
</style>