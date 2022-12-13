<%*
// **1. UPDATE HOME PAGE**

	let oldDashboardFile = await this.app.vault.getAbstractFileByPath("Wiki/index.md");
	let dashboardTemplate = await this.app.vault.getAbstractFileByPath("Wiki/Settings/Templates/tp/Dashboards/Index - Markdown Version.md");
	
	// DELETE CURRENT HOME PAGE
	await this.app.vault.trash(oldDashboardFile);
	
	// CREATE NEW HOME PAGE WITH UPDATED PROJECT TABLE
	let newDashboardFolder = await this.app.vault.getAbstractFileByPath("Wiki");
	let newDashboardFile = await tp.file.create_new(dashboardTemplate, "index", true, newDashboardFolder);

// **3. GIT PUSH = VAULT BACKUP  PUBLISH TO MKDOCS**
	app.commands.executeCommandById('obsidian-git:push');
_%>