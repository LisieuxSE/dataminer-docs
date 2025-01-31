---
uid: Web_apps_Feature_Release_10.3.6
---

# DataMiner web apps Feature Release 10.3.6 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to the web applications, see [General Feature Release 10.3.6](xref:General_Feature_Release_10.3.6).

## Highlights

*No highlights have been selected for this release yet*

## Other features

#### Low-code apps: Making an app execute actions by adding action configurations to the app's URL [ID_35979]

<!-- MR 10.4.0 - FR 10.3.6 -->

It is now possible to make an app execute one or more actions by adding action configurations to the app's URL.

To do so, proceed as follows:

1. Configure the action(s) in the action editor.
1. Click the *Copy actions* button to copy the action configuration to the Windows clipboard as a JSON object.
1. Add a `#` sign to the URL, and paste the JSON object in the URL.

When you add an action configuration to a URL of an app, the action(s) will immediately be executed. The app doesn't need to be reloaded. This way, even apps that are embedded in a visual overview can easily be forced to execute actions.

As soon as the actions have been executed, the action configuration will be removed from the URL to prevent them from being executed multiple times.

Example of an `Open a panel` action added to the URL of an app:

```txt
https://myDMA/APP_ID/PAGE_NAME#{"actions":[{"Type":6,"__type":"Skyline.DataMiner.Web.Common.v1.DMAApplicationPagePanelAction","Panel":"4507edc7-fcee-47bd-985c-f40d844e72cb","Position":"Center","Width":30,"AsOverlay":true}]}
```

> [!NOTE]
>
> - Making an app execute actions by adding a configuration to its URL does not work while that app is in edit mode.
> - Currently, the following actions cannot be executed this way for security reasons:
>
>   - `Execute a script`
>   - `Execute component action: delete current instance/save current changes`
>   - `Navigate to an URL`

#### Dashboards app & Low-code apps - Table and State components: New 'Initial selection' setting [ID_35984]

<!-- MR 10.4.0 - FR 10.3.6 -->

The *Table* and *State* components now have a new *Initial selection* setting.

When you enable this setting, the first entry of the GQI result set will automatically be selected when the dashboard or app is opened or refreshed.

> [!NOTE]
>
> - This new setting has also been added to the *Grid* component, which is only available if you activate the *ReportsAndDashboardsDynamicVisuals* soft-launch option.
> - For reasons of consistency, in the Drop-down feed, List feed, Parameter feed and Tree feed, the *Feed defaults* setting has now also been renamed to *Initial selection*

## Changes

### Enhancements

#### Legacy reports and dashboards will no longer be prefetched if the soft-launch option 'LegacyReportsAndDashboards' is set to false [ID_35881]

<!-- MR 10.4.0 - FR 10.3.6 -->

From now on, legacy reports and dashboards will no longer be prefetched if the soft-launch option *LegacyReportsAndDashboards* is set to false.

#### DataMiner web apps: Angular and other dependencies have been upgraded [ID_36100]

<!-- MR 10.4.0 - FR 10.3.6 -->

In all web apps (e.g. Low-code apps, Dashboards, Monitoring, Jobs, Ticketing, etc.), Angular and other dependencies have been upgraded.

### Fixes

#### Interactive Automation scripts: Problems with datetime component [ID_35682]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

When an interactive Automation script was launched from a web app, the following issues could occur. These were all related to the datetime web component (*UIBlockType.Time*):

- When you clicked a date in the datetime picker, a changed value would already be returned to the script. From now on, the selected datetime value will not be returned to the script until you close the picker (either by double-clicking or by clicking *Done*).

- The datetime value that was returned to the script when the component lost focus could be incorrect.

- The focus loss detection would not always be accurate.

#### Dashboards app & Low-code apps - Table component: Minimum pagesize would be used when exporting to a CSV file [ID_36012]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

When exporting data from a table component to a CSV file, the minimum pagesize would be used. From now, the largest possible pagesize is used when exporting data from a table component to a CSV file.

#### Dashboards app & Low-code apps: Component title could be made too large [ID_36021]

<!-- MR 10.2.0 [CU15]/10.3.0 [CU3] - FR 10.3.6 -->

In a custom component theme, for some fonts, the font size of the title could be set to a value higher than 36px, causing the component title to be larger than its container. Also, in some cases, the font size could incorrectly be set to 0px.

From now on, font sizes will have to be set to a value between 1px and 36px.

#### Dashboards app: Error when opening a shared dashboard containing a 'Line & area chart' component, a 'State' component, a 'Gauge' component or a 'Ring' component [ID_36022]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

An error could occur when you opened a shared dashboard that contained a *Line & area chart* component, a *State* component, a *Gauge* component or a *Ring* component.

#### Dashboards app: Retry button of table component would incorrectly be displayed in PDF file [ID_36026]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

When you generated a PDF of a dashboard that contained a table component showing a *Retry* button (because of an error in the table), then that *Retry* button would incorrectly also be displayed in the PDF file.

#### Dashboards app: Invalid nodes could get added to a GQI query [ID_36045]

<!-- MR 10.4.0 - FR 10.3.6 -->

In some cases, invalid nodes could get added to a GQI query, causing run-time errors to be thrown.

#### Web apps: Problem with single sign-on when embedded in Cube [ID_36049]

<!-- MR 10.4.0 - FR 10.3.6 -->

When the *Dashboards*, *Jobs* or *Ticketing* app was embedded in DataMiner Cube, in some cases, users would incorrectly be prompted to log in to the app.

#### Dashboards app & Low-code apps: Clearing a State component by means of CTRL+Click [ID_36056]

<!-- MR 10.4.0 - FR 10.3.5 -->

You can now clear a *State* component by clicking it while holding down the CTRL key.

#### Dashboards app & Low-code apps: GQI query nodes without options would incorrectly be expanded [ID_36064]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

In some cases, GQI query nodes without options would incorrectly be expanded.

#### Dashboards app: Problem when a 'State' component was fed a parameter value by a drop-down component in a shared dashboard [ID_36075]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

In a shared dashboard, an error could occur when a *State* component was fed a parameter value by a drop-down component.

#### Dashboards app & Low-code apps: GQI table component could throw 'Paged table session not found' error [ID_36101]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

In some cases, a GQI table component could thrown the following error:

```txt
Error trapped: Paged table session not found
```

From now on, a table session will immediately be closed after the last page has been fetched. This will prevent the above-mentioned error from being thrown.

#### Dashboards app: Error when opening a shared dashboard containing a 'Parameter Page' component [ID_36103]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

An error could occur when you opened a shared dashboard that contained a *Parameter Page* component.

#### Dashboards app & Low-code apps: Problem when searching elements of which the name contained special characters [ID_36128]

<!-- MR 10.3.0 [CU3] - FR 10.3.6 -->

When, while editing a dashboard, you opened the *ELEMENTS* section in the *DATA* tab, and entered an element name containing special characters in the search box, the result set would always be empty, even if elements with that name existed.

#### Dashboards app & Low-code apps: Popup panel showing a PDF preview would incorrectly have a scroll bar [ID_36131]

<!-- MR 10.2.0 [CU15]/10.3.0 [CU3] - FR 10.3.6 -->

In some cases, the popup panel showing the PDF preview of a dashboard would incorrectly have a scroll bar.

From now on, a popup panel showing a PDF preview will take the full screen height and will only allow its contents to scroll.
