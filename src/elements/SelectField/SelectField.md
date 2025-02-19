Select fields look like this. Yes, including the locale switcher.

```jsx { "props": { "className": "i18n-enabled" } }
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  color="orange"
  icon="vote-yea"
  :option-list="optionList"
  is-basic/>
```

### Color set

A select field, unless colored, is grey.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  :option-list="optionList"/>
```

Looks quite drab, we know. So they can be colored with any color from the set 
provided by CC Vocabulary.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<Grid>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="blue"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="green"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="magenta"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="olive"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="orange"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="purple"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="red"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="sand"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 4, 4, 4]">
    <SelectField
      color="yellow"
      :option-list="optionList"/>
  </GridCell>
</Grid>
``` 

Also you may use one of the three shades, namely `light`, `dark` and `darker`, 
to accentuate the color.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<Grid>
  <GridCell :span-set="[12, 6, 3, 3, 3]">
    <SelectField
      color="blue"
      shade="light"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 3, 3, 3]">
    <SelectField
      color="blue"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 3, 3, 3]">
    <SelectField
      color="blue"
      shade="dark"
      :option-list="optionList"/>
  </GridCell>
  <GridCell :span-set="[12, 6, 3, 3, 3]">
    <SelectField
      color="blue"
      shade="darker"
      :option-list="optionList"/>
  </GridCell>
</Grid>
```

On a dark or non-white background, the inverted version of the component should
be used.

```jsx { "props": { "className": "dark-background" } }
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<Grid>
  <GridCell :span-set="[12, 6, 6, 6, 6]">
    <SelectField
      :option-list="optionList"
      is-inverted/>
  </GridCell>
  <GridCell :span-set="[12, 6, 6, 6, 6]">
    <SelectField
      :option-list="optionList"
      is-inverted
      is-basic/>
  </GridCell>
  <GridCell :span-set="[12, 6, 6, 6, 6]">
    <SelectField
      color="magenta"
      :option-list="optionList"
      is-inverted/>
  </GridCell>
  <GridCell :span-set="[12, 6, 6, 6, 6]">
    <SelectField
      color="magenta"
      :option-list="optionList"
      is-inverted
      is-basic/>
  </GridCell>
</Grid>
```

### Add-on set

A select field can contain an icon to act as a visual aid as to what the choice
is about. Note that the icon must be added to the FontAwesome library by the
application.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  color="red"
  icon="vote-yea"
  :option-list="optionList"/>
```

If you'd like your own something there, you can override the add-on slot with 
something you like. This is not very flexible as there is a `1.25em` width limit
by default. To increase the limit, set the CSS custom property 
`--select-field-addons-space` on the element like so.

```css static
.vocab.select-field {
  ---select-field-addons-space: 2.5em;
}
```

See it in action.

```jsx
let optionList = [
  {
    value: 'by',
    text: 'CC BY'
  },
  {
    value: 'oth',
    text: 'Any other license'
  }
];

<SelectField
  color="green"
  style="--select-field-addons-space: 2.5em;"
  :option-list="optionList">
  <template #addons>
    <LicenseIconography :icon-list="['', 'by']"/>
  </template>
</SelectField>
```

### Style set

A select field can be defined to not attract attention, unless given attention
via means of a hover.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  color="orange"
  icon="vote-yea"
  :option-list="optionList"
  is-basic/>
```

A select field can be defined to deny attention, unless very specifically given
attention by the user.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  color="blue"
  icon="vote-yea"
  :option-list="optionList"
  is-ghost/>
```


### Size set

Select fields come in all sizes, from small to mega.

```jsx { "props": { "className": "contain-content" } }
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  color="purple"
  size="small"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="big"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="large"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="huge"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="enormous"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="gigantic"
  :option-list="optionList"/>
<br/><br/>
<SelectField
  color="purple"
  size="mega"
  :option-list="optionList"/>
```

### Indication set

A select field may indicate a negative, ambiguous or positive choice. For
example, in this case deleting permanently is a destructive action whereas
restoring to safety is not. The dropdown changes color to reflect this.

```jsx
let value = 'meh';
let options = [
  {value: 'del', text: 'Delete file'}, 
  {value: 'meh', text: 'Hide file'}, 
  {value: 'res', text: 'Keep file'}
];

<SelectField
  v-model="value"
  :indication="value === 'res' ? 'positive' : value === 'del' ? 'negative' : 'probably'"
  :option-list="options"/>
```

### State set

A select field may be disabled to prevent input altogether.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  :option-list="optionList"
  is-disabled/>
```

A select field may be made read-only to prevent input while maintaining 
readability as an output-only control.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  :option-list="optionList"
  is-read-only/>
```

### Attributes

All attributes that you could pass to an `select` tag can be passed to the 
`SelectField` component.

So a select field may have a `name` and a `value`.

```jsx
let optionList = [
  {
    value: 'a',
    text: 'Option A'
  },
  {
    value: 'b',
    text: 'Option B'
  }
];

<SelectField
  :option-list="optionList"
  name="Name"
  value="b"/>
```
