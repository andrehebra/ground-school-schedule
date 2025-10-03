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
    let privateClassDays = [0,1,2,3,4,5,6,7]; //0 indicates sunday etc
    function nextPrivateClasses() {
        let currentDate = new Date();
        let startDate = new Date(2025, 9, 12);
        let classIndex = 0;
        
        while (privateClasses.length < 150) {
            if (privateClassDays.includes(startDate.getDay())) {
                privateClasses.push({
                    lesson: privateSchedule[classIndex % privateSchedule.length],
                    date: new Date(startDate)
                });
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
        </div>
        <div class="gridItem">
            <h2>Commercial</h2>
        </div>
    </div>
</div>


<style>
    :global(.classGrid) {
        display: flex;
        justify-content: center;
        align-items: space-between;
    }
    :global(.gridItem) {
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
        width: 100%; /* Full width of the viewport */
        height: 100vh; /* Full height of the viewport */
        margin: 0;
        padding: 0;
    }
</style>