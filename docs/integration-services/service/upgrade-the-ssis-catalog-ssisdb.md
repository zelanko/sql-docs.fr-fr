---
title: "Mettre &#224; niveau le catalogue SSIS (SSISDB) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.dbupgradewizard.f1"
ms.assetid: 170c3dc9-f5bf-4599-ae56-d24a620f23e8
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Mettre &#224; niveau le catalogue SSIS (SSISDB)
  Exécutez l’Assistant Mise à niveau de SSISDB pour mettre à niveau la base de données du catalogue SSIS, SSISDB, quand celle-ci est plus ancienne que la version actuelle de l’instance SQL Server. Cela se produit quand l’une des conditions suivantes est remplie.  
  
-   Vous avez restauré la base de données à partir d’une ancienne version de SQL Server.  
  
-   Vous n’avez pas supprimé la base de données d’un groupe de disponibilité Always On avant la mise à niveau de l’instance SQL Server. Cela empêche la mise à niveau automatique de la base de données. Pour plus d'informations, consultez [Upgrading SSISDB in an availability group](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade).  
  
 L’assistant peut uniquement mettre à niveau la base de données sur une instance de serveur local.  
  
## Mettre à niveau le catalogue SSIS (SSISDB) en exécutant l’Assistant Mise à niveau de SSISDB  
  
1.  Sauvegardez la base de données du catalogue SSIS, SSISDB.  
  
2.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le serveur local puis développez **Catalogues Integration Services**.  
  
3.  Cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Mise à niveau de base de données** pour lancer l’Assistant Mise à niveau de SSISDB.  
  
     ![Launch the SSISDB upgrade wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-1.png "Launch the SSISDB upgrade wizard")  
  
4.  Sur la page **Sélectionner une instance** , sélectionnez une instance de SQL Server sur le serveur local.  
  
    > [!IMPORTANT]  
    >  L’assistant peut uniquement mettre à niveau la base de données sur une instance de serveur local.  
  
     Sélectionnez la case à cocher pour indiquer que vous avez sauvegardé la base de données SSISDB avant d’exécuter l’assistant.  
  
     ![Select the server in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-2.png "Select the server in the SSISDB Upgrade Wizard")  
  
5.  Sélectionnez **Mettre à niveau** pour mettre à niveau la base de données du catalogue SSIS.  
  
6.  Sur la page **Résultat** , passez en revue les résultats.  
  
     ![Review the results in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-3.png "Review the results in the SSISDB Upgrade Wizard")  
  
  