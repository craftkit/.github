
# Write your web app like a native app!

## craftkit is a new library for imperative programming on the web powered by the Shadow DOM

### Now is the time to move on to the Shadow DOM, throw the Virtual DOM out the window!

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

class Local extends Craft.UI.View {
    template(componentId) {
        return `
            <div class="root">Local</div>
        `;
    }
}

class World extends Craft.UI.View {
    template(componentId) {
        return `
            <div class="root">World</div>
        `;
    }
}
```
