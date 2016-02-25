py3中不再区分urllib和urllib2，同时，使用quote被放到了urllib.parse下，即不再使用urllib.quote()而是urllib.parse.quote()

py3字典排序不再使用
` keys = d.keys()
keys.sort()`
而是使用
` keys = sorted(d)`