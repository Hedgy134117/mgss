# MGSS
Minimal Generator of Static Sites

## Templating
- `{{ variable-name }}` for dynamic variable content
- `{% function-name:variable-name arguments %}` for running some function on some variable

## Functions
`{% list:variable-name element-type %}`
- Creates multiple elements of `element-type` from the list given by `variable-name`
- Example:
```python
# .py
technologies = ["python", "javascript"]
```
```html
<!-- HTML -->
<!-- Template -->
<ul>
    {% list:technologies li %}
</ul>
<!-- After Generation -->
<ul>
    <li>python</li>
    <li>javascript</li>
</ul>
```

`{% list-template:variable-name template-name %}`
- Creates multiple templates from the list given by `variable-name`
```python
# .py
projects = [
    Template(name="Project", desc="a simple project", technologies=["python", "javascript"]), 
    Template(name="Project 2", desc="a less simple project", technologies="rust")
]
```
```html
<!-- HTML -->
<!-- Document -->
<div class="projects">
    {% list-template:projects project %}
</div>
<!-- Project Template -->
<div>
    <h3>{{ name }}</h3>
    <p>{{ description }}</p>
    <p>Technologies used:</p>
    <ul>
        {% list:technologies li %}
    </ul>
</div>
<!-- After Generation -->
<div class="projects">
    <div class="project">
        <h3>Project</h3>
        <p>a simple project</p>
        <p>Technologies used:</p>
        <ul>
            <li>python</li>
            <li>javascript</li>
        </ul>
    </div>
    <div class="project">
        <h3>Project 2</h3>
        <p>a less simple project</p>
        <p>Technologies used:</p>
        <ul>
            <li>rust</li>
        </ul>
    </div>
</div>
```