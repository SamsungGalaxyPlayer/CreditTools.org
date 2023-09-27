---
title: "Submit new card"
layout: form-layout
---

<h1>{{ site.data.credit_card_template.title }}</h1>
<p>{{ site.data.credit_card_template.description }}</p>

<form id="creditCardSubmissionForm">
  {% for item in site.data.credit_card_template.fields %}
    {% assign field = item[0] %}
    {% assign context = item[1] %}
    {% assign title = context.title | default: field | capitalize %}
    {% assign description = context.description %}
    {% assign is_required = context.required | default: true %}
    
    <div class="field-group"> <!-- This is the wrapping div -->
        <label for="{{ field }}">{{ title }}{% if is_required %}<span class="required-asterisk">*</span>{% endif %}</label>
        {% if description %}
        <p class="field-description">{{ description }}</p>
        {% endif %}
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
    </div>
{% endfor %}

  <button type="button" onclick="generateGitHubIssueURL()">Generate GitHub Issue URL</button>
</form>

<script>
function validateForm() {
    const formData = new FormData(document.getElementById('creditCardSubmissionForm'));
    for (let pair of formData.entries()) {
        if (pair[1] === "" && document.getElementById(pair[0]).required) {
            alert(pair[0] + " is a required field!");
            return false;
        }
    }
    return true;
}

function generateGitHubIssueURL() {
    if (!validateForm()) {
        return;
    }

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
