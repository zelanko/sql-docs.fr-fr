---
title: Applets de commande PowerShell pour Reporting Services mode SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79fe1380a38ab9b2d309f0fc6419261e4f13ef8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75253264"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Applets de commande PowerShell pour le mode SharePoint de Reporting Services
  Lorsque vous installez [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] le mode SharePoint, les applets de commande PowerShell sont installées pour prendre en charge les serveurs de rapports en mode SharePoint. Les applets de commande couvrent trois catégories de fonctionnalités.  
  
-   Installation du service partagé et du proxy SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Configuration et gestion des applications de service et des proxys associés d' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Gestion des fonctionnalités d' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , par exemple extensions et clés de chiffrement.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Mode SharePoint|  
  
 **Cette rubrique contient les sections suivantes :**  
  
-   [Résumé des applets de commande](#bkmk_cmdlet_sum)  
  
-   [Applets de commande de service partagé et de proxy](#bkmk_sharedservice_cmdlets)  
  
-   [Applets de commande d’application de service et de proxy](#bkmk_serviceapp_cmdlets)  
  
-   [Reporting Services des applets de commande de fonctionnalités personnalisées](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Exemples de base](#bkmk_basic_samples)  
  
-   [Exemples détaillés](#bkmk_detailedsamples)  
  
    -   [Créer une application de service Reporting Services et un proxy](#bkmk_example_create_service_application)  
  
    -   [Analyse et mise à jour d'une extension de remise Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Obtenir et définir les propriétés de la base de données d'application Reporting Services, par exemple le délai d'expiration de la base de données](#bkmk_example_db_properties)  
  
    -   [Répertorier les extensions de données Reporting Services-mode SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Modifier et répertorier les propriétaires d'abonnement](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a>Résumé de l’applet de commande  

 Pour exécuter les applets de commande, vous devez ouvrir SharePoint Management Shell. Vous pouvez aussi utiliser l’éditeur d’interface utilisateur graphique fourni avec Microsoft Windows : **l’Environnement d’écriture de scripts intégré de Windows PowerShell (ISE)**. Pour plus d’informations, consultez [Démarrage de Windows PowerShell sur Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell). Dans les résumés d’applets de commande suivants, les références aux bases de données de l’application de service font référence à toutes les bases de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] données créées et utilisées par une application de service. Cela inclut la configuration, la définition d'alertes et les bases de données temp.  

  
 Si vous voyez un message d'erreur semblable au suivant lorsque vous tapez les exemples PowerShell :  
  
-   Install-SPRSService : Le terme 'Install-SPRSService' n'est pas reconnu comme  
    nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l’orthographe du nom ou, si un chemin d’accès a été inclus, vérifiez que le chemin d’accès est correct et réessayez.  
  
 Un des problèmes suivants se produit :  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'est pas installé et par conséquent, les applets de commande [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne sont pas installées.  
  
-   Vous avez exécuté la commande PowerShell dans Windows PowerShell ou Windows PowerShell ISE au lieu de SharePoint Management Shell. Utilisez SharePoint Management Shell ou ajoutez le composant logiciel enfichable SharePoint à la fenêtre Windows PowerShell à l'aide de la commande suivante :  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Pour plus d’informations, consultez [utiliser Windows PowerShell pour administrer SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Pour ouvrir SharePoint Management Shell et exécuter les applets de commande  
  
1.  Cliquez sur le bouton **Démarrer**  
  
2.  Cliquez sur le groupe **Produits Microsoft SharePoint** .  
  
3.  Cliquez sur **SharePoint Management Shell**.  
  
 Pour consulter l’aide sur la ligne de commande pour une applet de commande, utilisez la commande « Get-Help » de PowerShell à l’invite de commandes PowerShell. Par exemple :  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a>Applets de commande de service partagé et de proxy  
 Le tableau suivant contient les applets de commande PowerShell pour le service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint.  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Install-SPRSService|Installe et enregistre, ou désinstalle, le service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Cette opération peut être effectuée uniquement sur l'ordinateur qui dispose d'une installation de SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint. Pour l'installation, deux opérations ont lieu :<br /><br /> 1) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est installé dans la batterie de serveurs.<br /><br /> 2) l' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance de service est installée sur l’ordinateur actuel.<br /><br /> Pour la désinstallation, deux opérations ont lieu :<br />1) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est désinstallé de l’ordinateur actuel.<br />2) le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service est désinstallé de la batterie de serveurs.<br /><br /> <br /><br /> Remarque : si d'autres ordinateurs dans la batterie de serveurs ont le service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installée ou, si des applications de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] s'exécutent toujours dans la batterie de serveurs, un avertissement s'affiche.|  
|Install-SPRSServiceProxy|Installe et enregistre, ou désinstalle, le proxy du service Reporting Services dans la batterie de serveurs SharePoint.|  
|Get-SPRSProxyUrl|Obtient les URL pour accéder au service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Get-SPRSServiceApplicationServers|Obtient tous les serveurs dans la batterie SharePoint locale qui contiennent une installation du service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Cette applet de commande est utile pour les mises à niveau de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , car elle permet de déterminer quels serveurs exécutent le service partagé et doivent, par conséquent, être mis à niveau.|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> Applets de commande d'application de service et de proxy  
 Le tableau suivant contient les applets de commande PowerShell pour les applications de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et leurs proxys associés.  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Obtient un ou plusieurs objets d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSServiceApplication|Crée une application de service Reporting Services et des bases de données associées.<br /><br /> Paramètre LogonType : spécifie si le serveur de rapports utilise le compte de pool d'applications SSRS ou un compte de connexion SQL Server pour accéder à la base de données du serveur de rapports. Les valeurs possibles sont les suivantes :<br /><br /> 0 Authentification Windows<br /><br /> 1 SQL Server<br /><br /> 2. Compte du pool d'applications (valeur par défaut)|  
|Remove-SPRSServiceApplication|Supprime l'application de service Reporting Services spécifiée. Cela supprimera également les bases de données associées.|  
|Set-SPRSServiceApplication|Modifie les propriétés d'une base de données d'application de service Reporting Services existante.|  
|New-SPRSServiceApplicationProxy|Crée un nouveau proxy d'application de service Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Obtient un ou plusieurs proxys d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Dismount-SPRSDatabase|Démonte les bases de données d'application de service pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Remove-SPRSDatabase|Supprime les bases de données d'application de service pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Set-SPRSDatabase|Définit les propriétés des bases de données associées à une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Mount-SPRSDatabase|Monte les bases de données pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSDatabase|Crée les nouvelles bases de données d'application de service pour l'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] spécifiée.|  
|Get-SPRSDatabaseCreationScript|Génère le script de création de base de données à l'écran pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vous pouvez ensuite exécuter le script dans SQL Server Management Studio.|  
|Get-SPRSDatabase|Obtient une ou plusieurs bases de données d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Utilisez la commande pour obtenir l'ID de la base de données d'application de service afin d'utiliser l'applet de commande Set-SPRSDatabase pour modifier les propriétés, par exemple `querytimeout`. Consultez l'exemple de la rubrique, [Obtenir et définir les propriétés de la base de données d'application Reporting Services, par exemple le délai d'expiration de la base de données](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Génère le script des droits de la base de données à l'écran pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Invite à entrer l'utilisateur et la base de données souhaités, puis retourne un script Transact-SQL que vous pouvez exécuter pour modifier des autorisations. Vous pouvez ensuite exécuter ce script dans SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Génère un script de mise à niveau de base de données à l'écran. Le script met à niveau les bases de données d'application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] vers la version de la base de données de l'installation actuelle de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a>Reporting Services des applets de commande de fonctionnalités personnalisées  
  
|Applet de commande|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Met à jour la clé de chiffrement de l'application de service Reporting Services spécifiée et re-chiffre ses données.|  
|Restore-SPRSEncryptionKey|Restaure une clé de chiffrement précédemment sauvegardée pour une application de service Reporting Services.|  
|Remove-SPRSEncryptedData|Supprime les données chiffrées de l'application de service Reporting Services spécifiée.|  
|Backup-SPRSEncryptionKey|Sauvegarde la clé de chiffrement de l'application de service Reporting Services spécifiée.|  
|New-SPRSExtension|Enregistre une nouvelle extension avec une application de service Reporting Services.|  
|Set-SPRSExtension|Définit les propriétés d'une extension Reporting Services existante.|  
|Remove-SPRSExtension|Supprime une extension d'une application de service Reporting Services.|  
|Get-SPRSExtension|Obtient une ou plusieurs extensions d' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour une application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .<br /><br /> Les valeurs autorisées sont :<br /><br /> **Distribution**<br /><br /> **DeliveryUI**<br /><br /> **Render**<br /><br /> **Données**<br /><br /> **Sécurité**<br /><br /> **Authentification**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Définition**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Obtient les sites SharePoint en fonction de l'activation de la fonction « ReportingService ». Par défaut, les sites qui activent la fonction « ReportingService » sont retournés.|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a>Exemples de base  
 Retournez la liste des applets de commande qui contiennent « SPRS » dans le nom. Ce sera la liste complète des applets de commande de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 Ou bien, vous serez redirigés vers un fichier texte nommé commandlist.txt contenant plus de détails.  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Installez le service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint et le proxy de service.  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 Démarrer le service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Tapez la commande suivante à partir de SharePoint Management Shell pour retourner une liste filtrée des lignes du fichier journal. La commande filtre les lignes qui contiennent « ssrscustomactionerror ». Cet exemple consulte le fichier journal créé lorsque le fichier rssharepoint.msi a été installé.  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a>Exemples détaillés  
 En plus des exemples suivants, consultez la section « script Windows PowerShell » dans la rubrique [script Windows PowerShell pour les étapes 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a>Créer une application de service Reporting Services et un proxy  
 Cet exemple de script effectue les tâches suivantes :  
  
1.  Création d'une application de service Reporting Services et d'un proxy. Le script suppose que le pool d’applications « My App Pool » existe déjà.  
  
2.  Ajout du proxy au groupe de proxy par défaut  
  
3.  Octroi de l’accès à l’application de service à la base de données de contenu de l’application web sur le port 80. Le script suppose que le sitehttp://sitename«» existe déjà.  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a>Examiner et mettre à jour une extension de remise Reporting Services  
 L’exemple de script PowerShell suivant met à jour la configuration de l’extension de remise du courrier électronique par le serveur de rapports pour l’application de service nommée `My RS Service App`. Mettez à jour les valeurs du serveur SMTP (`<email server name>`) et de l’alias de messagerie électronique FROM (`<your FROM email address>`).  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 Dans l'exemple ci-dessus, si vous ne connaissiez pas le nom exact de l'application de service, vous pouvez réécrire la première instruction pour obtenir l'application de service en fonction d'une recherche portant sur son nom partiel. Par exemple :  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 Le script suivant retourne les valeurs de configuration actuelles pour l’extension de remise de courrier électronique du serveur de rapports pour l’application de service nommée « Application Reporting Services ». La première étape définit la valeur de la variable $app pour l'objet de l'application de service dont le nom est « My RS Service App ».  
  
 La deuxième instruction obtiendra l’extension de remise « Report Server Email » pour l’objet d’application de service dans la variable $app, puis sélectionne le configuration XML.  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 Vous pouvez réécrire les deux instructions ci-dessus dans une seule :  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a>Obtenir et définir les propriétés de la base de données d’application Reporting Services, par exemple le délai d’expiration de la base de données  
 L'exemple suivant renvoie d'abord une liste des bases de données et propriétés afin de déterminer le guid (ID) de base de données que vous fournissez à la commande. Pour obtenir une liste complète des propriétés, utilisez `Get-SPRSDatabase | format-list`.  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 Voici un exemple de sortie. Déterminez l'ID de la base de données que vous voulez modifier et utilisez l'ID de l'applet de commande SET.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Pour vérifier que la valeur est définie, réexécutez l'applet de commande GET.  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a>Répertorier les extensions de données Reporting Services-mode SharePoint  
 L'exemple suivant effectue une itération sur chaque application de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et répertorie les extensions de données actuelles.  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Exemple de sortie :**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a>Modifier et répertorier les propriétaires d’abonnements  
 Consultez [Utiliser PowerShell pour modifier et répertorier Reporting Services propriétaires d’abonnement et exécuter un abonnement](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser PowerShell pour modifier et répertorier Reporting Services propriétaires d’abonnement et exécuter un abonnement](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Liste de vérification : utiliser PowerShell pour vérifier PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint)   
 [Scripts PowerShell de gestion CodePlex SharePoint](https://sharepointpsscripts.codeplex.com/)   
