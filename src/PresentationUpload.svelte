<!--
<label for="presentation-file">Select a PowerPoint presentation:</label>
<input type="file" id="presentation-file" accept=".ppt,.pptx">
<button on:click={generateSummary}>Generate Summary</button>

<script>
  async function generateSummary() {
    const fileInput = document.getElementById('presentation-file');
    const file = fileInput.files[0];
    const contents = await readFile(file);
    console.log(contents);
    // TODO: Analyze the file contents and generate a summary
  }

  function readFile(file) {
    return new Promise((resolve, reject) => {
      const reader = new FileReader();
      reader.onload = () => resolve(reader.result);
      reader.onerror = reject;
      reader.readAsArrayBuffer(file);
    });
  }

  export PresentationUploader;
</script>
-->
<!-- Export the component -->
