
```javascript
//"#{변수명}"
const regex = /#{(\w+[.])*\w+}/g;

const replaceDate = (template, context) => {
	return template.replace(regex, (match) => getData(match, context));
}

const getData = (match, context) => {
	return match
	    .replace("#{", "")
        .replace("}", "")
        .split(".")
        .reduce((object, key) => object[key], context);
}

return replaceData(template, data)
```

