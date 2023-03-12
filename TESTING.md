# Testing Documentation

## Introduction
As of 3/12/2023, a CI/CD protocol has been completed for both our Dolphin and ASM repositories. This means a more clear direction for testing can now be laid out, allowing for more QA/Testing oriented folks to be of use!  

## Testing Steps
* If this is your first time testing, you will need to currently clone the ASM repo in order to obtain the launchers for a later step. Skip this step otherwise.
  - Enter the command `git clone https://github.com/Brawlback-Team/brawlback-asm.git` in a terminal under a directory you wish for a new folder `brawlback-asm` with the code to end up in.
  - The folder you need is called `Launchers` in the root this new directory after cloning.
* Download the artifacts from [Dolphin](https://github.com/Brawlback-Team/dolphin) and [ASM](https://github.com/Brawlback-Team/brawlback-asm).
  - If there is an associated PR for both, download both artifacts from the appropriate PRs. If there isn't one for one of either, download the most recent master artifact. This should be accessible via a green Checkmark on the **most recent commit** for that PR. If the checkmark for that commit is a red X, wait for the dev to update the PR so that it builds correctly.
  - Make sure to read the PR notes for ASM; it should be pretty easy to deduce if it's a PR related to Replays or the Netcode. **Only test the SD card for whatever feature is being tested, as the Netcode codes cannot coexist with the Replay codes in a testing environment currently; this is being addressed in a PR down the line. You will still need to ensure that changes made to one SD Card type doesn't break the others, I just isolated them for testing.**
* Ensure you have an appropriate Brawl REV1 ISO with a valid hash.
  - If you are unsure whether you have this, doublecheck with a member of the developer team in the #testing-general chat of the Brawlback discord.
* Unzip the artifacts with the program of your choice, we recommend 7Zip.
* Add the pf folder from P+ into SDCard/Project+.
  - Mount the SD Card from the P+ build; this is usually the sd.raw file located in the Wii folder under User.
  - Copy the pf folder from this build into the above folder.
* Place your Lylat.json file into the root of the Dolphin folder where the binary is.
  - This can be obtained by signing up for [lylat.gg](https://lylat.gg/) and then going [downloading the user file for Lylat](https://lylat.gg/users/enable).
* Open and setup the Dolphin build.
  - Set the appropriate graphics setting for your OS and graphics card. IE DX11 for Nvidia cards on Windows.
  - Add the folder where the ISO and launchers (from step 1) sits under Paths.
  - Set the Brawl ISO as your default ISO.
  - Setup the SD card folder and file. *I have listed the steps to do so from within Dolphin, but this is possible to achieve in other ways.*
    * Click the big `Config` button on the toolbar of Dolphin.
    * Browse to the Wii tab.
    * Under SD Card Settings, ensure `Insert SD Card` is checked.
    * Click the button with the dots next to the directory selector with the label `SD Sync Folder`.
    * Browse to the appropriate SDCard folder from the ASM artifact you downloaded and set it as the SD Sync Folder.
    * Click `Convert Folder to File Now`.
* Read the PR notes for testing instructions. If none are present, ask the developer what to do to test their PR in #testing-general.
* Start the appropriate launcher from the testing instructions and test extensively, making sure to check for niche issues, such as ICs desyncs.
* Add a comment to the PR noting any issues with some information about your OS and hardware that might be informative.

## Questions
To ask questions about various builds or general testing issues, join the [Brawlback discord](https://discord.gg/dzYRN32k4D) and pop an introduction into #dev-role-verification before posting in #testing-general.
