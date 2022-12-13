<%*
// **1. UPDATE HOME PAGE**

	let oldDashboardFile = await this.app.vault.getAbstractFileByPath("Wiki/index.md");
	let dashboardTemplate = await this.app.vault.getAbstractFileByPath("Wiki/Settings/Templates/tp/Dashboards/Index - Markdown Version.md");
	
	// DELETE CURRENT HOME PAGE
	await this.app.vault.trash(oldDashboardFile);
	
	// CREATE NEW HOME PAGE WITH UPDATED PROJECT TABLE
	let newDashboardFolder = await this.app.vault.getAbstractFileByPath("Wiki");
	let newDashboardFile = await tp.file.create_new(dashboardTemplate, "index", true, newDashboardFolder);
	
// **2. UPDATE PROBLEMS DASHBOARD**

	let oldProblemsDashboardFile = await this.app.vault.getAbstractFileByPath("Wiki/Problems Dashboard.md");
	let problemsDashboardTemplate = await this.app.vault.getAbstractFileByPath("Wiki/Settings/Templates/tp/Dashboards/Problems Dashboard - Markdown Version.md");
	
	// DELETE CURRENT PROBLEMS DASHBOARD
	await this.app.vault.trash(oldProblemsDashboardFile);
	
	// CREATE NEW PROBLEMS DASHBOARD
	let newProblemsDashboardFolder = await this.app.vault.getAbstractFileByPath("Wiki");
	let newProblemsDashboardFile = await tp.file.create_new(problemsDashboardTemplate, "Problems Dashboard", true, newProblemsDashboardFolder);
	
// **3. UPDATE TASKS DASHBOARD**

	let oldTasksDashboardFile = await this.app.vault.getAbstractFileByPath("Wiki/Tasks Dashboard.md");
	let tasksDashboardTemplate = await this.app.vault.getAbstractFileByPath("Wiki/Settings/Templates/tp/Dashboards/Tasks Dashboard - Markdown Version.md");
	
	// DELETE CURRENT TASKS DASHBOARD
	await this.app.vault.trash(oldTasksDashboardFile);
	
	// CREATE NEW TASKS DASHBOARD
	let newTasksDashboardFolder = await this.app.vault.getAbstractFileByPath("Wiki");
	let newTasksDashboardFile = await tp.file.create_new(tasksDashboardTemplate, "Tasks Dashboard", true, newTasksDashboardFolder);

// **4. UPDATE PARTNERS DASHBOARD**

	let oldPartnersDashboardFile = await this.app.vault.getAbstractFileByPath("Wiki/Projects/Partners/index.md");
	let partnersDashboardTemplate = await this.app.vault.getAbstractFileByPath("Wiki/Settings/Templates/tp/Dashboards/Partners Dashboard - Markdown Version.md");
	
	// DELETE CURRENT PARTNERS DASHBOARD
	await this.app.vault.trash(oldPartnersDashboardFile);
	
	// CREATE NEW PARTNERS DASHBOARD
	let newPartnersDashboardFolder = await this.app.vault.getAbstractFileByPath("Wiki/Projects/Partners");
	let newPartnersDashboardFile = await tp.file.create_new(partnersDashboardTemplate, "index", true, newPartnersDashboardFolder);

// **5. GIT PUSH = VAULT BACKUP  PUBLISH TO MKDOCS**
	app.commands.executeCommandById('obsidian-git:push');
_%>