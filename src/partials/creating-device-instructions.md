{% set image_path = [book.partials.images_path, '/creating_device_instructions'] | join %}

Open an existing or new project inside of UEFN. To create the custom device within your proejct, you need to open the Verse explorer.

![Opening the Verse Explorer]({{ image_path }}/open_verse_explorer.png)

This will open another window, which you can choose to dock anywhere in the interface.

![Verse Explorer Window]({{ image_path }}/verse_explorer.png)

Inside the Verse Explorer, right click on the `Content` folder and choose `Create New Verse File`.

![Create New Verse File Option]({{ image_path }}/new_verse_file.png)

After clicking the `Create New Verse File` button, you will be presented with another window to create the file. The name of this script for this example is `{{ creating_device_instructions.device_filename }}`. Then click the `Create` button to close the dialog window.

> Although you don't need to use the suffix `_device` for custom device scripts, it's good practice and makes it clear what this script is for.

![Create New Verse File Dialog]({{ image_path }}/create_new_verse_file.png)

{% include [book.partials.path, '/download-vs-code.md'] | join %}

Once you have VS Code installed on your computer, you can click the `Verse` button in the UEFN toolbar to open up your project in VS Code.
We will come back to the VS Code editor after setting up the other devices we will use in our script soon. For now, we will return to the UEFN editor.

![Open VS Code Verse]({{ image_path }}/open_vs_code_verse.png)

To be able to interact with your new device, you will need to compile the Verse script in your project. You can do that either by using the keyboard shortcut `CTRL+SHIFT+B` or by clicking the `Build Verse Code` button in the `Verse` window menu.

![Build Verse Code]({{ image_path }}/build_verse_code.png)

Once the code is built, you can find your new device in the `Content Browser` at the bottom of the UEFN editor. The filepath where it is stored is `All -> YourProjectName -> CreativeDevices`. Drag the new device into the viewport.

![Device In Viewport]({{ image_path }}/device_in_viewport.png)

If you don't want the device visible in the game when it's played, you can hide it by unchecking `Visible in Game` in the Details panel. If you don't see that in the details panel, click on the device in the viewport first. Make sure to keep `Enabled at Game Start` checked!

![Custom Device Detail Panel]({{ image_path }}/custom_device_dialog_menu.png)
