# Common action properties

Certain properties are shared across all actions, ensuring consistency and flexibility in configuration. These common properties allow you to define behaviors, appearance, and functionality that apply universally, regardless of the specific actions used. This simplifies the setup process and helps maintain uniformity across different jigs.

blalblcxlvxcvlcxvcxvcxxc

<table isTableHeaderOn="true" selectedColumns="" selectedRows="">
  <tr>
    <td>
      <p>Lists</p>
    </td>
    <td>
    </td>
    <td>
    </td>
  </tr>
  <tr>
    <td>
      <ol>
      <li>sadasdasda</li>
      <li>asdasdas</li>
      <li>dasdasdas
      <ol>
      <li>asdasdasda
      <ol>
      <li>aasdasdas</li>
      <li>asdasdasdas
      <ol>
      <li>asdasdasd</li>
      <li>asdasdasda</li>
      </ol>
      </li>
      </ol>
      </li>
      </ol>
      </li>
      </ol>
    </td>
    <td>
      <ul>
      <li>list</li>
      <li>asdasd</li>
      <li>asds
      <ul>
      <li>asdasdas</li>
      <li>sdasdas</li>
      <li>asdasda</li>
      <li></li>
      </ul>
      </li>
      </ul>
      <div></div>
      <div><p>asdaasdas</p></div>
      <div><p>asdasdaasd</p></div>
      <div><p>asdasdasas</p></div>
    </td>
    <td>
    </td>
  </tr>
  <tr>
    <td>
    </td>
    <td>
    </td>
    <td>
    </td>
  </tr>
  <tr>
    <td>
    </td>
    <td>
    </td>
    <td>
    </td>
  </tr>
</table>



1. Line 1
2. Line2
   1. Line1a
   2. line2a
      1. line3a
         1. line3b
      2. Checkbox
      3. bla bla bla
      4. bla bla  la

- [x] checked
- [ ] not-checked

## Icons in actions

Adding an `icon` property in an action only applies to `swipeable`, `secondary`, and `header` actions. Primary actions do not support icon setups.

## Working with parent & child actions

&#x20;When configuring actions across parent and child jigs, the following behavior applies:

- If both the parent and child jigs have an `action` configured, the child’s configuration takes precedence and overrides the parent’s.
- If only the parent has an `action`, it automatically applies to the child.
- If only the child has an `action`, it is used in the parent jig as well.

## Dual action buttons

::::VerticalSplit{layout="middle"}
:::VerticalSplitItem
Configure `actions` to display two action buttons on the jig's main screen. In this example, the first button has a secondary button `style` applied, by default, the button normally uses the primary color. Additionally, you can set up a third action, referred to as a secondary action button, that appears when the ellipsis (...) is tapped. This allows multiple action options to be accessible within a single jig.
:::

:::VerticalSplitItem
![Dual action buttons & secondary button](https://qa.archbee.co/api/optimize/0TQnKgJpsWhT3gQzQOhdY-TZVU6r07hz0LEPo_3zZ2W-20250225-092012.png "Dual action buttons & secondary button")
:::
::::

| **Property**             | **Description**                                                                                                                                      |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `numberOfVisibleActions` | Configure this property to display multiple action buttons on the screen. The recommended number is two. A numerical value is expected, such as `2`. |

```yaml
actions:
# Number of visible buttons displayed on the jig.
  - numberOfVisibleActions: 2       
    children:
      # First action button.
      - type: action.go-back
        options:
          # Apply a style to the button. 
          style:
            isSecondary: true
          title: Back
      # Second action button.                
      - type: action.go-to
        options:
          title: Continue
          behaviour: new
          linkTo: contact  
      # Third action button configured (secondary action).
      # The button displays when the ellipsis is tapped.    
      - type: action.execute-entity
        options:
          title: Save  
          provider: DATA_PROVIDER_DYNAMIC
          entity: default/contacts
          method: create
          data:
            firstName: =@ctx.components.firstName.state.value
            lastName: =@ctx.components.lastName.state.value
            email: =@ctx.components.email.state.value
            phone: =@ctx.components.phone.state.value
            jobTitle: =@ctx.components.jobTitle.state.value
            companyName: =@ctx.components.companyName.state.value    
```

