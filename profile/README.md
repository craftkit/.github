# Write web apps as if they're native apps!

## Craftkit is a cutting-edge library designed for imperative programming on the web, harnessing the power of the Shadow DOM. 

### It's time to embrace the Shadow DOM and leave the Virtual DOM behind!

<img width="1351" alt="code2" src="https://user-images.githubusercontent.com/4404088/198875149-1f19c63a-1e90-455f-8132-fe8a0605e58e.png">

<details>
  <summary>Show as text</summary>

```js
class Greeting extends Craft.UI.View {
    constructor() {
        super();
        this.views = {
            local: new Local(),
            world: new World()
        };
    }
    viewDidLoad(callback) {
        this.appendView({
            id: "whom",
            component: this.views.local
        });
        if (callback) { callback(); }
    }
    greet() {
        this.replaceView({
            id: "whom",
            component: this.views.world
        });
    }
    style(componentId) {
        return `
            .container { display: flex; flex-direction: row; }
        `;
    }
    template(componentId) {
        return `
            <div class="root">
                <div class="container>
                    <div>Hello</div>
                    <div id="whom"></div>
                </div>
                <button onclick="${componentId}.greet()">Greet</button>
            </div>
        `;
    }
}

class HelloPlace extends Craft.UI.View {
    constructor() {
        super();
        this.data = { place: "Any Where" };
    }
    style(componentId) {
        return `
            .msg { color: blue; }
        `;
    }
    template(componentId) {
        return `
            <div class="root">
                <span class="msg">${this.data.place}<\span>
            </div>
        `;
    }
}

class Local extends HelloPlace {
    constructor() {
        super();
        this.data = { place: "Local" };
    }
}

class World extends HelloPlace {
    constructor() {
        super();
        this.data = { place: "World!" };
    }
    style(componentId) {
        return super.style(componentId) + `
            .msg { color: red; }
        `;
    }
}
``` 

</details>
