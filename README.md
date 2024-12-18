# Configuring Your Repository

After creating a new repository based on this template, make sure to update your
repository settings to enable Workflows to write to the repository. If you
don't, then auto updates for TamperMonkey won't work.

To enable write permissions for Workflows, go to `Settings > Actions > General`
and under the Workflow permissions section, enable Read and Write permissions.

# Configuring Your TamperMonkey Script

In the `userscript-headers.json` file, make sure to update the properties as
needed for your TamperMonkey script. This json is used to populate a
UserscriptPlugin object, which creates the necessary userscript header comments
after webpack finishes compiling. See the
[UserscriptPlugin](https://github.com/momocow/webpack-userscript?tab=readme-ov-file#load-headers)
repository for more details.

The script version will automatically update whenever a change is made to the
main branch.

# Installing the TamperMonkey script

To install the TamperMonkey script, simply go to the `dist/script.user.js` file
in github and click on the "Raw" link to the code.

# Debugging locally

Step 1: run `npm install` to get all the dependencies
Step 2: run `npx webpack` to compile the script
Step 3: copy the `dist/script.user.js` file to your TamperMonkey script editor

# Sample TM script

### Main App Component:

```javascript
import { createComponent } from './miniFramework';
import { Container } from './components/container.component';
import { Button } from './components/button.component';
import { Title } from './components/title.component';

export const App = createComponent(() => {
  return Container({
    children: [
      Title({
        text: 'Sample Title',
      }),
      Button({
        id: 'submit-btn',
        text: 'Submit',
        onClick: () => alert('Submit button clicked'),
      }),
    ],
  });
});
```

### Other components

```javascript
import { createElement, createComponent } from '../miniFramework';

export const Button = createComponent(({ id, text, onClick }) =>
  createElement('button', { id, onClick }, text)
);
```
