
# 冒泡排序

```
var arr = ['D','C','B','A'];
var m,i;
var len = arr.length;
for (m=0;m<len-1;m++){
	let blen = len - m -1;
	for (i=0;i<blen;i++){
        if(arr[i].charCodeAt() > arr[i+1].charCodeAt()) {
            let t = arr[i+1];
            arr[i+1] = arr[i];
            arr[i] = t;
        } else {
            continue;
        }
	}
}
```