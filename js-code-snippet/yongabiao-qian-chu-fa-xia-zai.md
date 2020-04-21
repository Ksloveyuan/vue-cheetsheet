# 用a标签触发下载



{% tabs %}
{% tab title="有response" %}
```javascript
const data = "test string"
const blob = new Blob([data], { type: 'text/plain' })
const link = document.createElement('a')
link.href = window.URL.createObjectURL(blob)
link.setAttribute('target', '_blank')
link.download = 'accountSummary.txt'
document.body.appendChild(link)
link.click()
setTimeout(() => {
  document.body.removeChild(link)
}, 0)
```
{% endtab %}

{% tab title="有Url" %}
```javascript
const link = document.createElement('a')
link.href = url
link.setAttribute('target', '_blank')
link.download = name
document.body.appendChild(link)
link.click()
setTimeout(() => {
  document.body.removeChild(link)
}, 0)
```
{% endtab %}
{% endtabs %}

