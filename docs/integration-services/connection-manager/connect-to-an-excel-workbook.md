---
title: "&#201;tablir une connexion &#224; un classeur Excel | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Excel [Integration Services]"
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# &#201;tablir une connexion &#224; un classeur Excel
  Pour connecter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à un classeur Microsoft Office Excel, vous devez utiliser un gestionnaire de connexions Excel.  
  
 Vous pouvez créer ces gestionnaires de connexions à partir de la zone Gestionnaires de connexions dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou à partir de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Fournisseurs et pilotes pour fichiers Microsoft Excel et Access**  
  
 Vous devrez peut-être télécharger les fournisseurs et pilotes OLE DB pour les fichiers Microsoft Office, s’ils ne sont pas installés. Les versions ultérieures du fournisseur peuvent ouvrir des fichiers créés par les versions antérieures d’Excel.  
  
 Si l’ordinateur contient une version 32 bits de Microsoft Office, vous devez installer la version 32 bits des pilotes et vérifier que vous exécutez l’assistant ou le package Services d’intégration qu’il crée en mode 32 bits.  
  
|Version de Microsoft Office|Télécharger|  
|------------------------------|--------------|  
|2007|[Pilote Office System 2007 : composants de connectivité de données](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
### Pour créer un gestionnaire de connexions Excel à partir de la zone Gestionnaires de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package.  
  
2.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** et sélectionnez **Nouvelle connexion**.  
  
3.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **Excel**, puis configurez le gestionnaire de connexions.  
  
     Pour plus d’informations sur les options de configuration qui sont disponibles pour ce gestionnaire de connexions, consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### Pour créer une connexion à Excel à partir de l'Assistant Importation et Exportation SQL Server  
  
1.  Démarrez la version 32 bits de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans la page **Choisir une source de données**, pour **Source de données**, sélectionnez **Microsoft Excel**, puis configurez la connexion à Excel.  
  
     Pour plus d’informations sur les options de configuration qui sont disponibles pour ce type de connexion, consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## Voir aussi  
 [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  