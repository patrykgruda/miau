# miau
<h2>Schemat Hornera</h2>
<pre>
<code>
def horner(coefficients, x):
    result = 0
    for coefficient in coefficients:
        result = result * x + coefficient
    return result
</code>
</pre>
<button class="copy-btn">Kopiuj kod</button>

<script src="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.11/clipboard.min.js"></script>
<script>
new ClipboardJS('.copy-btn', {
    text: function(trigger) {
        return `def horner(coefficients, x):
    result = 0
    for coefficient in coefficients:
        result = result * x + coefficient
    return result`;
    }
});
</script>
