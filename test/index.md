# TEst
<script>
const { execSync } = require('child_process');

const output = execSync('ls', { encoding: 'utf-8' });

console.log('The output is:');
console.log(output);
</script>
