---
title: "&#201;tablir une connexion &#224; une base de donn&#233;es Access | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Access [Integration Services]"
  - "bases de données Access [Integration Services]"
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# &#201;tablir une connexion &#224; une base de donn&#233;es Access
  Connecter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à une source de données Microsoft Office Access requiert un gestionnaire de connexions OLE DB et un fournisseur de données. Le fournisseur de données que vous utilisez dépend de la version d’Access qui a été utilisée pour créer la source de données :  
  
-   Pour Access 2003 et les versions antérieures, le package nécessite le fournisseur OLE DB pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
-   Pour Access 2007, le package requiert le fournisseur OLE DB pour le moteur de base de données Microsoft Office Access 12.0.  
  
 Vous pouvez créer un gestionnaire de connexions OLE DB et sélectionner le fournisseur de données correspondant à partir de la zone Gestionnaires de connexions dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou à partir de l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access en mode 32 bits. Les deux fournisseurs OLE DB pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet et pour le moteur de base de données Microsoft Office Access 12.0 sont disponibles uniquement dans des versions 32 bits.  
  
## Connexion à une source de données dans Access 2003 ou un format antérieur  
  
#### Pour créer un gestionnaire de connexions Access à partir de la zone Gestionnaires de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package.  
  
2.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** et choisissez **Nouvelle connexion OLE DB**.  
  
3.  Dans la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**, cliquez sur **Nouveau**.  
  
     Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Dans la boîte de dialogue **Gestionnaire de connexions**, pour **Fournisseur**, sélectionnez **Fournisseur OLE DB pour Microsoft Jet 4.0**, puis configurez le gestionnaire de connexions comme il convient.  
  
#### Pour créer une connexion à Access à partir de l'Assistant Importation et exportation SQL Server  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], démarrez l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans la page **Choisir une source de données**, pour **Source de données**, sélectionnez **Microsoft Access**, puis configurez la connexion à Access.  
  
     Quand vous sélectionnez **Microsoft Access** comme **Source de données**, l’Assistant crée automatiquement le gestionnaire de connexions OLE DB nécessaire avec le fournisseur de données correct. Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## Connexion à une source de données dans le format Access 2007  
 Pour accéder à une source de données Access 2007, le gestionnaire de connexions OLE DB requiert le fournisseur OLE DB pour le moteur de base de données Microsoft Office Access 12.0. Ce fournisseur est installé automatiquement avec la version 2007 de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office System. Si le système Office 2007 n'est pas installé sur l'ordinateur sur lequel [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] s'exécute, vous devez installer le fournisseur séparément. Pour installer le fournisseur OLE DB pour le moteur de base de données Microsoft Office Access 12.0, téléchargez et installez les composants fournis dans la page web [Pilote d’Office System 2007 : composants de connectivité des données](http://go.microsoft.com/fwlink/?LinkId=98155).  
  
#### Pour créer un gestionnaire de connexions OLE DB à partir de la zone Gestionnaires de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package.  
  
2.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** et choisissez **Nouvelle connexion OLE DB**.  
  
3.  Dans la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**, cliquez sur **Nouveau**.  
  
     Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Dans la boîte de dialogue **Gestionnaire de connexions**, pour **Fournisseur**, sélectionnez **Fournisseur OLE DB du moteur de base de données Microsoft Office Access 12.0**, puis configurez le gestionnaire de connexions comme il convient.  
  
    > [!NOTE]  
    >  Pour établir une connexion à une source de données qui utilise Access 2007, vous ne pouvez pas sélectionner **Fournisseur OLE DB pour Microsoft Jet 4.0** comme **Source de données**.  
  
#### Pour créer une connexion OLE DB à partir de l'Assistant Importation et exportation SQL Server  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], démarrez l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans la page **Choisir une source de données**, pour **Source de données**, sélectionnez **Fournisseur OLE DB du moteur de base de données Microsoft Office Access 12.0**, puis configurez la connexion comme il convient.  
  
    > [!NOTE]  
    >  Pour établir une connexion à une source de données qui utilise Access 2007, vous ne pouvez pas sélectionner **Fournisseur OLE DB pour Microsoft Jet 4.0** comme **Source de données**.  
  
     Quand vous sélectionnez **Fournisseur OLE DB du moteur de base de données Microsoft Office Access 12.0** comme **Source de données**, l’Assistant crée automatiquement le gestionnaire de connexions OLE DB nécessaire avec le fournisseur de données correct. Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## Voir aussi  
 [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  