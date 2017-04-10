---
title: "Bo&#238;te de dialogue d&#39;ex&#233;cution de package | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.ispackageexecute.f1"
  - "sql13.ssis.ssms.executepackage.f1"
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Bo&#238;te de dialogue d&#39;ex&#233;cution de package
  Utilisez la boîte de dialogue **Exécuter le package** pour exécuter un package stocké sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peut contenir des paramètres qui référencent les valeurs stockées dans les variables d'environnement. Avant d'exécuter un tel package, vous devez spécifier quel environnement sera utilisé pour fournir les valeurs de variable d'environnement. Un projet peut contenir plusieurs environnements, mais un seul environnement peut être utilisé pour la liaison de valeurs de variable d'environnement au moment de l'exécution. Si aucune variable d'environnement n'est utilisée dans le package, un environnement n'est pas obligatoire.  
  
 Que voulez-vous faire ?  
  
-   [Ouvrir la boîte de dialogue Exécuter le package](#open_dialog)  
  
-   [Définir les options sur la page Général](#general)  
  
-   [Définir les options de l'onglet Paramètres](#parameters)  
  
-   [Définir les options de l'onglet Gestionnaires de connexions](#connection)  
  
-   [Définir les options de l'onglet Avancé](#advanced)  
  
-   [Création de script avec les options de la boîte de dialogue Exécuter le package](#script)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Exécuter le package  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous vous connectez à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données SSISDB.  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **SSISDB** .  
  
4.  Développez le dossier contenant le package à exécuter.  
  
5.  Cliquez avec le bouton droit sur le package, puis cliquez sur **Exécuter**.  
  
##  <a name="general"></a> Définir les options sur la page Général  
 Sélectionnez **Environnement** pour spécifier l'environnement qui est appliqué avec le package.  
  
##  <a name="parameters"></a> Définir les options de l'onglet Paramètres  
 Utilisez l'onglet **Paramètres** pour modifier les valeurs de paramètre utilisées lors de l'exécution du package.  
  
##  <a name="connection"></a> Définir les options de l'onglet Gestionnaires de connexions  
 Utilisez l'onglet Gestionnaires de connexions pour définir les propriétés du ou des gestionnaires de connexions du package.  
  
##  <a name="advanced"></a> Définir les options de l'onglet Avancé  
 Utilisez l'onglet Avancé pour gérer des propriétés et d'autres paramètres du package.  
  
 **Ajouter**, **Modifier**, **Supprimer**  
 Cliquez pour ajouter, modifier ou supprimer une propriété.  
  
 **Niveau de journalisation**  
 Sélectionnez le niveau de journalisation pour l'exécution du package. Pour plus d’informations, consultez [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md).  
  
 **Vider en cas d'erreurs**  
 Spécifiez si un fichier de vidage est créé lorsque des erreurs se produisent pendant l'exécution du package. Pour plus d’informations, voir [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).  
  
 **Runtime 32 bits**  
 Indiquez que le package doit s'exécuter sur un système 32 bits.  
  
##  <a name="script"></a> Création de script avec les options de la boîte de dialogue Exécuter le package  
 Lorsque vous vous trouvez dans la boîte de dialogue **Exécuter le package** , vous pouvez également utiliser le bouton **Script** de la barre d'outils pour écrire du code [!INCLUDE[tsql](../../includes/tsql-md.md)] . Le script généré appelle les procédures stockées [catalog.start_execution &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) avec les options que vous avez sélectionnées dans la boîte de dialogue **Exécuter le package**. Le script s'affiche dans une nouvelle fenêtre de script dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
  