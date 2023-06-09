<script>
    let skills = [];
    let name = "";
    let masteryHours = 10000;

    let isAddMode = false;

    function clearAddForm() {
        name = "";
        isAddMode = false;
    }

    function createSkill(name) {
        let newSkill = {
            name: name,
            progress: 300,
        };
        skills = [...skills, newSkill];

        clearAddForm();
        computeProgress(newSkill.progress);
    }

    function computeProgress(progress) {
        let percentage = (progress / masteryHours) * 100;
        alert(percentage);
    }
</script>

{#if isAddMode}
    <div class="skillForm">
        <input type="text" name="name" id="name" bind:value={name} />
        <button on:click={() => createSkill(name)}>+</button>
    </div>
{/if}

<ul>
    {#each skills as skill}
        <li>{skill.name}</li>
    {/each}
</ul>

<button on:click={() => (isAddMode = true)}>Create Skill</button>

<style>
    .skillForm {
        display: flex;
    }
</style>
