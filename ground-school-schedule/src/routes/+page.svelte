<script>
    import { Heading, P } from 'flowbite-svelte';

    const privateSchedule = [
        {
            lesson: "Pilot Documents",
            tasks: ["Aircraft Documents", "Aircraft Inspections"],
        },
        {
            lesson: "Preflight Inspection",
            tasks: ["Checklist Usage", "Passenger Briefing", "Positive Exchange of Flight Controls"],
        },
        {
            lesson: "Operation of Systems",
            tasks: ["Primary Flight Controls", "Secondary Flight Controls"],
        },
        {
            lesson: "Operation of Systems",
            tasks: ["Powerplant", "Engine Oil", "Ignition"],
        },
        {
            lesson: "Operation of Systems",
            tasks: ["Fuel"],
        },
        {
            lesson: "Operation of Systems",
            tasks: ["Electrical"],
        },
        {
            lesson: "Safety Procedures",
            tasks: ["Radio Communications", "Taxi Procedures", "Runway Incursion Avoidance", "Cockpit Management"],
        },
        {
            lesson: "Safety Procedures",
            tasks: ["Collision Avoidance", "Practice Areas", "Fuel and Weather Requirements", "Minimum Safe Altitudes"],
        },
        {
            lesson: "Aerodynamics",
            tasks: ["Lift Production", "Drag Production", "Stalls", "Wake Turbulence Avoidance"],
        },
        
    ];

</script>

<div class="container">
    <h1 class="title">GROUND SCHOOL</h1>
</div>


<style>
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