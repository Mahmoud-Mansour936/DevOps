# 04-Jinja file

- Dynamic file that has variables i need to change more than one time → So instead of changing all variables or change the file every time just change the variables in playbook
- Its files with **.j2** extension
- Using **template** module to activate jinja2 file

## Variables

```yaml
{{ variable }} # like bash script
```

## If statement

```yaml
{% if_condition %}
# logic
{% elif_condition %}
#logic
{% else %}
#logic
{% endif %} # to end the statement
```

## For loop

```yaml
{% for item in list %}
# logic --> to iterate over module (list) we use the same way like item.key 
# but it will be ( list_name.key )

{% endfor %} # to end the loop

```