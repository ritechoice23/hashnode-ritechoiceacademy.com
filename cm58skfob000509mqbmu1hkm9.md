---
title: "Setting Up Scheduler in AdonisJS"
datePublished: Sat Dec 28 2024 23:07:13 GMT+0000 (Coordinated Universal Time)
cuid: cm58skfob000509mqbmu1hkm9
slug: setting-up-scheduler-in-adonisjs
tags: js, backend, queue, adonisjs

---

The `adonisjs-scheduler` package makes it easy to define and manage recurring tasks in AdonisJS applications. In this guide, we’ll walk through the installation, configuration, defining schedules, and running the scheduler in both development and production environments.

---

## Getting Started

### Step 1: Install the Package

Install the scheduler package using npm:

```bash
npm install adonisjs-scheduler
```

### Step 2: Configure the Package

Run the configuration command to set up the scheduler in your project:

```bash
node ace configure adonisjs-scheduler
```

This command generates the necessary files and configurations.

---

## Running the Scheduler

You can start the scheduler with the following commands:

### Run Scheduler

To run the scheduler and execute scheduled tasks:

```bash
node ace scheduler:run
```

### Run Scheduler with Worker Mode

Worker mode ensures tasks are handled efficiently and managed as jobs:

```bash
node ace scheduler:work
```

### Watch Mode (Development)

To automatically restart the scheduler when files are modified during development:

```bash
node ace scheduler:run --watch
```

### Running Scheduler in Production

To run the scheduler in a production environment and ensure it remains active, use PM2:

```bash
pm2 start "node ace scheduler:run"
```

This ensures the scheduler process is managed and restarts automatically if it fails.

---

## Defining Schedules

Schedules are defined in the `start/scheduler.ts` file. Here’s an example:

### Example Scheduler Definition

```typescript
import scheduler from 'adonisjs-scheduler/services/main';
import PurgeUsers from '../commands/purge_users';

// Schedule a command to run every five seconds
scheduler.command('inspire').everyFiveSeconds();

// Schedule a custom command with arguments
scheduler.command(PurgeUsers, ['30 days']).everyFiveSeconds().withoutOverlapping();

// Group schedules with overlapping protection
scheduler.withoutOverlapping(
  () => {
    scheduler.command('inspire').everySecond();
    scheduler.command(PurgeUsers, ['30 days']).everyFiveSeconds();
  },
  { expiresAt: 30_000 } // Set overlapping expiration
);

// Call a custom function weekly
scheduler
  .call(() => {
    console.log('Purge DB!');
  })
  .weekly();
```

### Key Features

* **Command Scheduling**: Use the `.command()` method to schedule AdonisJS commands.
    
* **Without Overlapping**: Ensure tasks do not run simultaneously by using `.withoutOverlapping()`.
    
* **Custom Function Calls**: Schedule custom logic with the `.call()` method.
    

---

## Conclusion

With `adonisjs-scheduler`, managing recurring tasks becomes straightforward. Following this guide, you can set up schedules, execute tasks efficiently, and manage them in production using PM2. For advanced configurations, refer to the package’s documentation.