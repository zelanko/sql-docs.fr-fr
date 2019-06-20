---
title: Supprimer une application de la couche Données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5b8b6b1d5975ff94fda98784449330571cc93cec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62872718"
---
# <a name="delete-a-data-tier-application"></a>Supprimer une application de la couche Données
  Vous pouvez supprimer une application de la couche Données à l'aide de l'Assistant Supprimer l'application de la couche Données ou d'un script Windows PowerShell. Vous pouvez spécifier si la base de données associée doit être conservée, détachée ou supprimée.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour mettre à niveau une DAC à l’aide de**  [l’Assistant d’inscription de l’application de la couche Données](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Lorsque vous supprimez une instance d'application de la couche Données (DAC), vous choisissez l'une des trois options qui spécifient le mode de traitement de la base de données associée à l'application de la couche Données. Les trois options suppriment les métadonnées de définition de la DAC. Les options diffèrent de par ce qu'elles font de la base de données associée à l'application de couche Données. L'Assistant ne supprime aucun des objets au niveau de l'instance associés à la DAC ou base de données, tels que les connexions.  
  
|Option|Actions de base de données|  
|------------|----------------------|  
|Supprimer l'inscription|La base de données associée reste intacte.|  
|Détacher la base de données|La base de données associée est détachée. L'instance du moteur de base de données ne peut pas référencer la base de données, mais les données et les fichiers journaux sont intacts.|  
|Supprimer la base de données|La base de données associée est supprimée. Les données et fichiers journaux sont supprimés.|  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Il n'existe aucun mécanisme automatique pour restaurer les métadonnées de définition de la DAC ou la base de données après avoir supprimé une DAC. La possibilité de reconstruire l'instance de la DAC manuellement dépend de l'option de suppression.  
  
|Option|Comment reconstruire l'instance de la DAC|  
|------------|-------------------------------------|  
|Supprimer l'inscription|Enregistrez une DAC de la base de données laissée en place.|  
|Détacher la base de données|Rattachez la base de données à l'aide de **sp_attachdb** ou de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis enregistrez une nouvelle instance de la DAC à partir de la base de données.|  
|Supprimer la base de données|Restaurez la base de données à partir d'une sauvegarde complète effectuée avant que la DAC ait été supprimée, puis enregistrez une nouvelle instance de la DAC à partir de la base de données.|  
  
> [!WARNING]  
>  La reconstruction d'une instance de la DAC en inscrivant une DAC à partir d'une base de données rattachée ou restaurée ne recréera pas certaines parties de la DAC d'origine, telles que la stratégie de sélection du serveur.  
  
###  <a name="Permissions"></a> Autorisations  
 Une DAC peut uniquement être supprimée par les membres des rôles serveur fixes **sysadmin** ou **serveradmin** , ou par le propriétaire de la base de données. Le compte d’administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré nommé **sa** peut également lancer l’Assistant.  
  
##  <a name="UsingDeleteDACWizard"></a> Utilisation de l'Assistant Supprimer l'application de la couche Données  
 **Pour supprimer une DAC à l'aide d'un Assistant**  
  
1.  Dans l' **Explorateur d'objets**, développez le nœud pour l'instance qui contient la DAC à supprimer.  
  
2.  Développez le nœud **Gestion** .  
  
3.  Développez le nœud **Applications de la couche Données** .  
  
4.  Cliquez avec le bouton droit sur la DAC à supprimer et sélectionnez **Supprimer une application de la couche Données**.  
  
5.  Renseignez les boîtes de dialogue de l'Assistant :  
  
    1.  [Introduction](#Introduction)  
  
    2.  [Choisir une méthode](#Choose_method)  
  
    3.  [Résumé](#Summary)  
  
    4.  [Supprimer une application de couche Données](#Delete_datatier_application)  
  
##  <a name="Introduction"></a> Page Introduction  
 Cette page décrit les étapes de la suppression d'une application de couche Données.  
  
 **Ne plus afficher cette page.** - Cochez la case pour ne plus afficher la page à l'avenir.  
  
 **Suivant >** : passe à la page **Choisir une méthode**.  
  
 **Annuler** : termine l’Assistant sans supprimer une application de couche Données ni une base de données.  
  
##  <a name="Choose_method"></a> Page Choisir une méthode  
 Utilisez cette page pour spécifier l'option pour gérer la base de données associée à la DAC à supprimer.  
  
 **Supprimer l’inscription** : supprime les métadonnées qui définissent l’application de couche Données, mais laisse la base de données associée intacte.  
  
 **Détacher la base de données** : supprime les métadonnées qui définissent l’application de couche Données et détache la base de données associée.  
  
 La base de données ne peut plus être référencée par cette instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)], mais les données et fichiers journaux restent intacts.  
  
 **Supprimer la base de données** : supprime les métadonnées qui définissent la DAC et supprime la base de données associée.  
  
 Les données et fichiers journaux pour la base de données sont supprimés définitivement.  
  
 **\< Précédent** : renvoie à la page **Introduction** .  
  
 **Suivant >** : passe à la page **Résumé**.  
  
 **Annuler** : termine l’Assistant sans supprimer la DAC ni la base de données.  
  
##  <a name="Summary"></a> Page Résumé  
 Utilisez cette page pour examiner les mesures prises par l'Assistant lors de la suppression de l'instance de la DAC.  
  
 **Examinez le résumé de vos sélections** : examinez la DAC, la base de données et la méthode de suppression affichées dans la fenêtre. Si les informations sont correctes, sélectionnez **Suivant** ou **Terminer** pour supprimer la DAC. Si la DAC et les informations sur la base de données ne sont pas correctes, sélectionnez **Annuler** , puis la DAC appropriée. Si la méthode de suppression n'est pas correcte, sélectionnez **Précédent** pour retourner à la page **Choisir une méthode** et sélectionner une méthode différente.  
  
 **\< Précédent** : renvoie à la page **Choisir une méthode** pour choisir une méthode de suppression différente.  
  
 **Suivant >** : supprime l’instance de la DAC en utilisant la méthode que vous avez choisie à la page précédente, puis passe à la page **Supprimer une application de couche Données**.  
  
 **Annuler** : termine l’Assistant sans supprimer l’instance de la DAC.  
  
##  <a name="Delete_datatier_application"></a> Page Supprimer une application de couche Données  
 Cette page signale la réussite ou l'échec de l'opération de suppression.  
  
 **Suppression de la DAC** : signale la réussite ou l’échec de chaque mesure prise pour supprimer l’instance de la DAC. Examinez les informations pour déterminer la réussite ou l'échec de chaque action. Toute action pour laquelle une erreur s'est produite aura un lien dans la colonne **Résultat** . Sélectionnez le lien pour consulter le rapport de d'erreur de cette action.  
  
 **Enregistrer le rapport** : sélectionnez ce bouton pour enregistrer le rapport de suppression dans un fichier HTML. Le fichier signale l'état de chaque action, notamment toutes les erreurs générées par chacune des actions. Le dossier par défaut est un dossier SQL Server Management Studio\DAC Packages dans le dossier Documents de votre compte Windows.  
  
 **Terminer** : termine l’Assistant.  
  
##  <a name="DeleteDACPowerShell"></a> Supprimer une DAC à l'aide de PowerShell  
 **Pour supprimer une DAC à l'aide d'un script PowerShell**  
  
1.  Créez un objet serveur SMO et définissez-le sur l'instance qui contient la DAC à supprimer.  
  
2.  Ouvrez un objet `ServerConnection` et connectez-vous à la même instance.  
  
3.  Utilisez `add_DacActionStarted` et `add_DacActionFinished` pour vous abonner aux événements de mise à niveau de la DAC.  
  
4.  Spécifiez la DAC à supprimer.  
  
5.  Utilisez l'un des trois jeux de codes, en fonction de l'option de suppression qui convient le mieux :  
  
    -   Pour supprimer l'inscription de la DAC, mais laisser la base de données intacte, utilisez la méthode `Unmanage()`.  
  
    -   Pour supprimer l'inscription de la DAC et détacher la base de données, utilisez la méthode `Uninstall()` et spécifiez `DetachDatabase`.  
  
    -   Pour supprimer l'inscription de la DAC et supprimer la base de données, utilisez la méthode `Uninstall()` et spécifiez `DropDatabase`.  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a>Exemple de suppression de la DAC mais en laissant la base de données (PowerShell)  
 L'exemple suivant supprime une DAC nommée MyApplication à l'aide de la méthode `Unmanage()` pour supprimer la DAC, mais laisser la base de données intacte.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a>Exemple de suppression de la DAC en détachant la base de données (PowerShell)  
 L'exemple suivant supprime une DAC nommée MyApplication à l'aide de la méthode `Uninstall()` pour supprimer la DAC et détacher la base de données.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a>Exemple de suppression de la DAC en supprimant la base de données (PowerShell)  
 L'exemple suivant supprime une DAC nommée MyApplication à l'aide de la méthode `Uninstall()` pour supprimer la DAC et la base de données.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de la couche Données](data-tier-applications.md)   
 [Applications de la couche Données](data-tier-applications.md)   
 [Déployer une application de la couche Données](deploy-a-data-tier-application.md)   
 [Inscrire une base de données en tant que DAC](register-a-database-as-a-dac.md)   
 [Sauvegarde et restauration des bases de données SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)  
  
  
