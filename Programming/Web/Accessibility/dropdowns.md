## Types of dropdown

- Menu: A list of commands or actions that the user can perform within the page content.
- Navigation: A list of links used for navigating through a website.
- Select: A form control (```<select>```) that displays a list of options for the user to select within a form.

## Navigation
- Don’t use ARIA menu semantics in navigation menu systems.
- On content heavy sites, don’t hide structure away in nested dropdown-powered navigation menus.
- Use aria-expanded to indicate the open/closed state of a button-activated navigation menu.
- Make sure said navigation menu is next in focus order after the button that opens/closes it.
- Never sacrifice usability in the pursuit of JavaScript-free solutions. It’s vanity.

## Menu
```html
<button aria-haspopup="true" aria-expanded="false">
  Difficulty
  <span aria-hidden="true">&#x25be;</span>
</button>
<div role="menu">
  <button role="menuitem">Easy</button>
  <button role="menuitem">Medium</button>
  <button role="menuitem">Incredibly Hard</button>
</div>
```
- ARIA menus are not designated for navigation but for application behavior. Imagine the menu system for a desktop application.
- The aria-haspopup property simply indicates that the button secretes a menu. It acts as warning that, when pressed, the user will be moved to the “popup” menu. Its value does not change — it remains as true at all times.
- The <span> inside the button contains the unicode point for a black down-pointing small triangle. This convention indicates visually what aria-haspopup does non-visually — that pressing the button will reveal something below it. The aria-hidden="true" attribution prevents screen readers from announcing “down pointing triangle” or similar. Thanks to aria-haspopup, it’s not needed in the non-visual context.
The aria-haspopup property is complemented by aria-expanded. - This tells the user whether the menu is currently in an open (expanded) or closed (collapsed) state by toggling between true and false values.
- The menu itself takes the (aptly named) menu role. It takes descendants with the menuitem role. They do not need to be direct children of the menu element, but they are in this case — for simplicity.

## Select requirements
- There is a button that contains the current selected option.
- Clicking the box toggles the visibility of the options list (also called listbox).
- Clicking an option in the listbox updates the selected value. The button text changes and the listbox is closed.
- Clicking outside the component closes the listbox.
- The trigger contains a small triangle icon pointing downward to indicate there are options.

## Hybrid select technique

- https://css-tricks.com/striking-a-balance-between-native-and-custom-select-elements/

## On menus and menu buttons

- https://inclusive-components.design/menus-menu-buttons/