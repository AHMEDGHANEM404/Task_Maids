# Task_Maids
### Documentation

All relevant documentation can be found in the Documentation folder.

### REFrameWork Template

**Robotic Enterprise Framework (REFramework)**

- Built on the *Transactional Business Process* template
- Utilizes a *State Machine* layout for the automation phases
- Provides advanced logging, exception handling, and recovery features
- Manages external settings via the *Config.xlsx* file and Orchestrator assets
- Retrieves credentials from Orchestrator assets and *Windows Credential Manager*
- Fetches transaction data from an Orchestrator queue and updates the transaction status
- Captures screenshots in the event of system exceptions

### How It Works

1. **INITIALIZE PROCESS**
   - `./Framework/InitiAllSettings` - Loads configuration data from the *Config.xlsx* file and Orchestrator assets
   - `./Framework/GetAppCredential` - Retrieves credentials from Orchestrator assets or the local Windows Credential Manager
   - `./Framework/InitiAllApplications` - Opens and logs into the applications used throughout the process

2. **GET TRANSACTION DATA**
   - `./Framework/GetTransactionData` - Fetches transactions from an Orchestrator queue specified in *Config.xlsx* (OrchestratorQueueName) or any other configured data source

3. **PROCESS TRANSACTION**
   - `Process` - Processes transactions and invokes other workflows related to the automation process
   - `./Framework/SetTransactionStatus` - Updates the status of the processed transaction (default: Orchestrator transactions) to Success, Business Rule Exception, or System Exception

4. **END PROCESS**
   - `./Framework/CloseAllApplications` - Logs out of and closes the applications used during the process

### Setting Up a New Project

1. Review and customize the *Config.xlsx* file with any necessary fields and values.
2. Implement `InitiAllApplications.xaml` and `CloseAllApplications.xaml` workflows, ensuring they are linked correctly in the *Config.xlsx* file.
3. Develop `GetTransactionData.xaml` and `SetTransactionStatus.xaml` workflows tailored to the transaction types being utilized (default is Orchestrator queues).
4. Create the `Process.xaml` workflow and integrate other workflows pertinent to the automation process.

---
AHmed Ghanem
