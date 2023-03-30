<script>
    const name = 'Julia Casado';
    const fav_things = ['music', 'friends', 'coffee'];
    const student = { name, fav_things };
</script>
  
<!--- HTML markup --->
<p>My name is {student.name} and these are some of my favourite things:</p>
<ul>
    {#each student.fav_things as f}
    <li>{f}</li>
    {/each}
</ul>