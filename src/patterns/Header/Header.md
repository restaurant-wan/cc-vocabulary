The header has a standard layout and appearance. It sits flush with the 
[Footer](#/Patterns/Footer) component, thanks to the use of 
[Container](#/Layouts/Container).

```jsx { "props": { "className": "i18n-enabled contain-content" } }
import { library } from '@fortawesome/fontawesome-svg-core';
import { 
  faHome,
  faBook,
  faSearch
} from '@fortawesome/free-solid-svg-icons';

library.add(faSearch, faHome, faBook);

<Header 
  title="Vocabulary" 
  color="blue">
  <InputField
    color="blue"
    :icon-set="['', 'search']"
    is-basic
    is-infused
    type="text"
    placeholder="Search..."/>
  <Navigation
    is-inverted>
    <NavigationLink icon="home">
      Home page
    </NavigationLink>
    <NavigationLink icon="book">
      Documentation
    </NavigationLink>
  </Navigation>
</Header>
<Footer/>
```

### Add-on set

Without specifying any app, the header shows the CC wordmark.

```jsx { "props": { "className": "contain-content" } }
<Header color="orange"/>
```

The name of the site and the URL to which the branding points can be passed to 
the header via the `title` and `homeUrl` props, converting the CC wordmark to
the CC lettermark.

```jsx { "props": { "className": "contain-content" } }
<Header
  color="red"
  title="Vocabulary"
  homeUrl="https://opensource.creativecommons.org/"/>
```

If the standard site naming does not catch your fancy, you can simply populate
the branding slot with something that does. Try not to deviate too much from the
standard template.

The right side contains a slot so that you can populate your own content in it.
Ideally you would use this space to place a [Navigation](#/Elements/Navigation)
component or a search box or the user profile. But those are just suggestions.

Anything goes.

```jsx { "props": { "className": "contain-content" } }
<Header color="green">
  <template #branding>
    <BrandImagery
      color="white"
      type="letterheart"
      size="small"
      is-centered/>
    <BrandImagery
      color="white"
      brand="vocabulary"
      size="small"
      is-centered/>
  </template>
  <div>
    <Heading :level="6">You really mean anything?</Heading>
    Yes, <em>literally</em> anything.
  </div>
</Header>
```

### Color set

A header without the color specified is black.

```jsx { "props": { "className": "contain-content" } }
<Header
  title="Default"/>
```

After having seen so many component you already know, the header can be colored
using any color from the set provided by CC Vocabulary.

Also you may use one of the two shades, namely `dark` and `darker`, to
accentuate the color. Note that `light` is present and works, just looks
terrible and it is not recommended unless you heavily customise the component.

Feel free to choose any color and shade of your choice, except maybe orange.
Let's leave orange for the [main site](https://creativecommons.org), shall we?

```jsx { "props": { "className": "contain-content" } }
import { library } from '@fortawesome/fontawesome-svg-core'
import { faFillDrip, faSwatchbook } from '@fortawesome/free-solid-svg-icons'

library.add(faFillDrip, faSwatchbook);

let color = '';
let colorOptions = [
  { value: '', text: 'None' },
  { value: 'blue', text: 'Blue' },
  { value: 'green', text: 'Green' },
  { value: 'magenta', text: 'Magenta' },
  { value: 'olive', text: 'Olive' },
  { value: 'orange', text: 'Orange' },
  { value: 'purple', text: 'Purple' },
  { value: 'red', text: 'Red' },
  { value: 'sand', text: 'Sand' },
  { value: 'yellow', text: 'Yellow' }
];

let shade = '';
let shadeOptions = [
  { value: '', text: 'Default' },
  { value: 'dark', text: 'Dark' },
  { value: 'darker', text: 'Darker' }
];

<SelectField
  v-model="color"
  :color="color ? color : null"
  icon="fill-drip"
  :option-list="colorOptions"/>
<SelectField
  v-model="shade"
  :color="color ? color : null"
  :shade="shade ? shade : null"
  icon="swatchbook"
  :option-list="shadeOptions"
  :is-disabled="color === ''"/>
<br/>
<br/>
<Header
  :color="color ? color : null"
  :shade="shade ? shade : null"
  title="App name"/>
```
