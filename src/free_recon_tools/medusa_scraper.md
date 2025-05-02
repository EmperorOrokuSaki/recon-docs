# <a href="https://getrecon.xyz/tools/medusa" target="_blank" rel="noopener noreferrer">Medusa Log Scraper</a>

![Medusa Logs Scraper](../images/tools/medusa.png)

## Medusa Web Tool
A web-based utility for converting Medusa fuzzing logs into Foundry test cases.

## Overview
This tool allows you to easily convert Medusa fuzzing logs into executable Foundry test cases. It automatically extracts function calls from your logs and generates test functions that can reproduce the exact conditions under which your smart contract properties failed.

## How It Works
1. **Paste your Medusa logs:** Copy and paste the logs generated at the end of your Medusa test run
2. **Automatic extraction:** All function calls will be scraped automatically from the pasted logs
3. **Test generation:** Each property will generate a Foundry reproducer unit test
4. **Configure options:** Toggle cheatcodes as needed to reproduce the exact state

## Features
- **Automatic log parsing:** Extracts relevant information from Medusa fuzzing logs
- **Foundry test generation:** Creates ready-to-use Foundry test files
- **VM state reproduction:** Includes options for block numbers, timestamps, and transaction senders
- **Address formatting:** Properly formats Ethereum addresses with checksums
- **Byte value handling:** Correctly formats byte values with proper hex prefixes
- **Multiple property support:** Handles multiple broken properties in a single log file

## Usage Instructions
### Step 1: Paste Your Medusa Logs
Copy the entire log output from your Medusa fuzzing run and paste it into the text area. For best results, make sure to include the section after "Fuzzer stopped, test results follow below...".

### Step 2: Configure VM Options
Toggle the following options as needed:

- **Block Numbers (vm.roll):** Include commands to set block numbers
- **Timestamps (vm.warp):** Include commands to set block timestamps
- **Transaction Senders (vm.prank):** Include commands to set transaction senders

### Step 3: Generate Tests
Click the "Generate Tests" button to create Foundry test functions based on your logs.

### Step 4: Copy and Use
Copy the generated test functions and paste them into your Foundry test file. These tests will reproduce the exact conditions that caused your properties to fail.

### Technical Implementation
The web tool is built on top of the [Pog Parser](https://github.com/Recon-Fuzz/log-parser) package, which provides specialized functions for processing Medusa logs:

- **Log Processing:** Uses `processLogs()` with Fuzzer.MEDUSA to extract information from raw logs

- **Function Conversion:** Uses `medusaLogsToFunctions()` to convert logs to test functions

- **VM Data Handling:** Configurable options for including VM state manipulations
