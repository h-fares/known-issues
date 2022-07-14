# known-issues

## Access to localhost was denied on MAC
### The problem:
You try to get http://localhost:7000 or http://localhost:5000 in Chromium and you get this error mesage _Access denied_ with HTTP-Code 403
### Why?
The issue turned out to be coming from the AirPlay receiver listening on Ports 5000 and 7000, which was creating the 403 error.
### Solution
* Be sure that localhost is pointed to 127.0.0.1: by checking the hosts file `sudo nano /etc/hosts`. This line has to be written: `127.0.0.1 localhost`
* Uncheck the "AirPlay Receiver": Go to System Perferences -> Sharing and uncheck the AirPlay Receiver.

[stackoverflow](https://stackoverflow.com/questions/33524826/localhost-not-working-in-chrome-127-0-0-1-does-work)


## Avoid mutating a prop
### The problem:
You get allways an error in the console `[Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders`.
### Why?
The reason behind this error is: you try to make changes on props that you get from parents component.
For example: 
```javascript
export default Vue.component('child-component', {
    props: {
        color: {
            type: object
        }
    },
    methods: {
        changeColor(newColor) {
            this.color = newColor
        }
    }
})
```
### Solution
Create a computed property that has changes.
```javascript
export default Vue.component('child-component', {
    props: {
        color: {
            type: object
        }
    },
    computed: {
        changedColor(newColor) {
            return newColor
        }
    }
})
```

### PS: Mutating props in Vue is an anti-pattern
[Resources](https://michaelnthiessen.com/avoid-mutating-prop-directly/)
