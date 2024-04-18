# mubu-bindings

Wrappers to access data from a MuBu container in other languages: Python, Javascript, etc.

High-level usage:

1. create an object of class Mubu, either:
- from a json file saved in Max
- from a .mubu file in SDIF format
- later: from a network connection to a Max process

2. create an objet of class MubuTrack to access the data

## Proposed API

Modeled after the existing mubujs binding within Max

### Mubu Constructor

- ...

### Mubu Properties

- numbuffers
- numtracks
- mubuname
- bufferindex
- trackindex

### Mubu Methods

- refer(mubuname)
- gettrack(bufferindex, trackid) ---> trackid == trackindex or trackname
- addtrack(maxsize, mxrows, mxcols, configsym) config symbol with @attributes like in message boxes
- inserttrack(index, maxsize, mxrows, mxcols, configsym)
- appendtrack(maxsize, mxrows, mxcols, configsym)
- removetrack(trackid) ---> trackid == trackindex or trackname
- movetrack(trackid, toindex)
- modifytrack(bufferindex, trackid, configsym)
- clonetrack(bufferindex, trackid, configsym)
- clonetrackto(bufferindex, trackid, destmubu, destbuffer, configsym)
- clearall()
- addbuffer([buffername])
- insertbuffer(bufferindex [buffername])
- movebuffer(fromindex, toindex)
- removebuffer(index)
- clearbuffer(index)
- getbufferinfo(index, key) ---> with no key get all infos
- setbufferinfo(index, key, value ...)
- clearbufferinfo(index)
- copybuffer(bufferindex , [starttime, endtime]) --> without startime/endtime copy the whole buffer
- pastebuffer(bufferindex, [starttime, endtime])
- cutbuffer(bufferindex, [starttime, endtime])
- addtrackpaste(bufferindex)
- addbufferpaste()
- readall(filepath, options)
- readbuffer(bufferindex, filepath, options)
- readappend(filepath, options)
- readtrack(bufferindex, trackid, filepath, options)
- readtrackappend(bufferindex, trackid, filepath, options)
- readfolder(filepath, options)
- writeall(filepath, options)
- writebuffer(bufferindex, filepath, options)
- writetrack(bufferindex, trackid, filepath, options)

### MubuTrack Constructor

- ...

### MubuTrack Properties

- name
- size
- mxcols
- mxrows
- timetagged
- haslabels
- maxsize
- samplerate
- sampleperiod
- sampleoffset

### MubuTrack Methods


- refer(nubuname, bufferindex, trackindex)
- release()
- clear()
- clearall()
- get(startindex, num)
- set(startindex, values)
- gettime(startindex, num)
- settime(startindex, values)
- getmatrix(startindex, num)
- setmatrix(startindex, values)
- getmxcolumn(columnindex, startindex, num)
- getmxrow(rowindex, startindex, num)
- setmxcolumn(columnindex, startindex, values)
- setmxrow(rowindex, startindex, values)
- getlabel(startindex, num)
- setlabel(startindex, values)
- getinfo(key)-->with key==NULL returns all infos
- setinfo(keys, values) if values == NULL unset key info
- insert(startindex, num, values) with values== NULL fill with 0.0
- append(num, values) with values== NULL fill with 0.0
- remove(startindex, num)
- getindex(time)
- getnextindex(time)
- getfloatindex(time)
- fill(time, values, label)
- filltime(time, [timestep]) without timestep use track->sampleperiod as increment
- fillmatrix(values) values --> 1 or more values (with 1 fillall with this value)
- filllabel(label)
- copy(startime, endtime)
- cut(starttime, endtime)
- paste(starttime, endtime)
- read(filepath)
- readappend(starttime, endtime)
- write(starttime, endtime)
- getmean(row, col)
- getmedian(row, col)
- getstdev(row, col)
- getmin(row, col)
- getmax(row, col)
- resample(sr)
