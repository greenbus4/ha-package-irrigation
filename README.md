# Sprinkler/Irrigation - for Home Assistant

## Overview
This is a set of YAML *packages* for running Irrigation programs. It is roughtly based off of one of the more
common Irrigation integrations. There were bugs in that integration (e.g. could not turn off valves at time!)
and wanted to be able to easily customize for my own use.

I've been moving more integrations into packages because HA really provides all the tools necessary to do many
things that integrations provide, and can group all needed automations, scripts, helpers and template into a single
file or directory.

* Valves are the physical switch to turn on or off an irrigatoin valve
* Programs are collections of valves, with either a default runtime or specific runtime for each valve


Existing Features:
* Define programs and and runtimes in a YAML config. This is currently in a script just to make it dead simple
* Define schedules using the standard Home Assistant Calendar
* Manually run individual programs or individual valves and specify a time to run that valve.
* View list of upcoming scheduled program runs
* Disable scheulde and set a date to automatically enable the schedule again.
* Adjust all programs times based on a percentage. External automations can change this based on rain or forecast.

To Do:
* Consider moving config into a template sensor attribute (but consider the size limits on attributes)
* The entire "programs" idea is based on physical programs. Might be better instead to define each valve separately
  with a time and frequency and then every day the system builds the day's program.
* Add UI elements to this repo
* Clean all the comments out of the packages. Hey, I talk to myself when writing...

## Screenshots

<details><summary>Click to view screenshots</summary>

***
*This section allows selecting a program and tracks the running state of a running program:*


<img width="543" height="492" alt="image" src="https://github.com/user-attachments/assets/fafdecb5-509b-4dc4-94f6-c3f16ef1aece" />

***
*The selected program details can be viewed:*

<img width="530" height="265" alt="image" src="https://github.com/user-attachments/assets/e573187d-e903-4ab1-a935-97f4a2ad2157" />

***
*Individual valves can be selected and run and can be marked as excluded from a program:*

<img width="543" height="357" alt="image" src="https://github.com/user-attachments/assets/c2b35f74-dcc4-4b0d-a70e-be9abc8972fc" />

***
*The upcoming schedule can be viewed:*

<img width="516" height="440" alt="image" src="https://github.com/user-attachments/assets/d5ea0bdc-913c-4109-bf67-c04b29ca6ed6" />

***
*Monitor current water flow and pressure and recent usage:*

<img width="551" height="565" alt="image" src="https://github.com/user-attachments/assets/29532232-9166-473d-b2ce-98255563d354" />

***
*The Logbook is used to track events:*

<img width="518" height="443" alt="image" src="https://github.com/user-attachments/assets/bb37c536-9ea5-418b-a9ab-e1f2ee4860a6" />

***
*Finally, a settings card:*

<img width="532" height="383" alt="image" src="https://github.com/user-attachments/assets/0225b802-f8b0-445b-84b5-a03174e77b62" />

</details>

## Concepts

## UI Requirement

### HACS
 * wget -O - https://get.hacs.xyz | bash -
 * add the integration
 * authorize with gihub (why?)

* text-divider-row (used on the raw switch page)
* uix and the uix integration
* logbook-card

To use the scheduling (`sprinkler_schedule.yaml`)
* Install `Local Calendar` integrations
* Create a calendar named "Irrigation"

And the monitoring has a `notify.sprinkler_log`
(This wasn't working on 2026.8.2)
* add the directory to `configuration.yaml`
```
  allowlist_external_dirs:
    - "/config"
```
* Add the `File` integration and setup `sprinkler.log` as an output
* rename the created entity to `notify.sprinkler_log`





