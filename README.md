# AddressBook

## Requirements and Running
Requires Python3.x and bottle (v0.12.13), once python is installed bottle can be installed using:<br/> 
`pip install bottle==0.12.13`<br/>
Once installed, the application can be ran using:<br/>
`python website.py`

## Features
AddressBook is a simple online contact keeper. Contacts can either be a person or an organisation, membership of the latter can be controlled through the contact's view.

## Code
Technologies used: Python (bottle framework), html, javascript, sqlite3 <br/>
Using the bottle framework, urls are directed using view functions to specific template files. The template files access their information using a content-dictionary, the requirements of which are displayed at the top of each template.<br/>
### Example view:
```python
#basic home-page, utilies a 'base' template for further expansion.
#   content-dictionary in the form:
#   {people: [a,b,...], orgs: [x,y,...], title: 'Address Book', text: 'Browse existing contacts or make a new one.'}
@route('/')
def main():
    contdict = getAll()
    contdict['title'] = 'Address Book'
    contdict['text'] = 'Browse existing contacts or make a new one.'

    return template('base.tpl', contdict=contdict)
```
### Example template:
```html
% # basic template for a title and text, require content-dictionary:
% # {... title: 'text-title', text: 'body-text'}

% include('header.tpl')
  <div id="main">
    <h2>{{contdict['title']}}</h2>
    {{contdict['text']}}
  </div>
% include('footer.tpl')
```
### Result
