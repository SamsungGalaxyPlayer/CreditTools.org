---
title: "Submit new card"
---

<h1>{{ site.data.credit_card_template.title }}</h1>
<p>{{ site.data.credit_card_template.description }}</p>

<form id="creditCardSubmissionForm">
  {% for item in site.data.credit_card_template.fields %}
    {% assign field = item[0] %}
    {% assign context = item[1] %}
    {% assign title = field | capitalize %}
    {% assign is_required = context.required | default: true %}
    <label for="{{ field }}">{{ title }}</label>
    {% if context.type == "boolean" %}
        <select name="{{ field }}" id="{{ field }}">
            <option value="true">True</option>
            <option value="false">False</option>
        </select>
    {% elsif context.type == "list" %}
        <select name="{{ field }}" id="{{ field }}">
            {% for value in context.values %}
                <option value="{{ value }}">{{ value }}</option>
            {% endfor %}
        </select>
    {% else %}
        <input type="{{ context.type }}" name="{{ field }}" id="{{ field }}" {% if context.max_length %}maxlength="{{ context.max_length }}"{% endif %} {% if is_required %}required{% endif %}>
    {% endif %}
  {% endfor %}
  <button type="button" onclick="generateGitHubIssueURL()">Generate GitHub Issue URL</button>
</form>

<script>
function generateGitHubIssueURL() {
    let baseURL = "https://github.com/{owner}/{repo}/issues/new?";
    let title = "New Card Submission: " + document.getElementById('card_name').value;
    let body = "";

    const formData = new FormData(document.getElementById('creditCardSubmissionForm'));
    for (let pair of formData.entries()) {
        body += pair[0] + ": " + pair[1] + "\n";
    }

    let issueURL = baseURL + "title=" + encodeURIComponent(title) + "&body=" + encodeURIComponent(body);
    window.location.href = issueURL;
}
</script>
