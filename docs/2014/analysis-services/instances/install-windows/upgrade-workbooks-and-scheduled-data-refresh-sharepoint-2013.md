---
title: Mettre à niveau les classeurs et l’actualisation planifiée des données (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: da4e685a1ebc05e27070873b12de99e8cc480a31
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543871"
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a>Mettre à niveau les classeurs et l'actualisation planifiée des données (SharePoint 2013)
  Cette rubrique traite de l'utilisation des classeurs créés dans les environnements PowerPivot précédents et comment mettre à niveau les classeurs PowerPivot afin de pouvoir tirer parti des nouvelles fonctionnalités introduites dans cette version. Pour en savoir plus sur les nouvelles fonctionnalités, consultez [Nouveautés de PowerPivot](https://go.microsoft.com/fwlink/?LinkID=203917).  
  
> [!WARNING]  
>  Vous ne pouvez pas restaurer la mise à niveau de classeurs qui sont mis à niveau automatiquement sur le serveur. Une fois qu'un classeur est mis à niveau, il le reste. Pour utiliser une version antérieure, vous pouvez republier le classeur précédent dans SharePoint, restaurer une version antérieure ou recycler le classeur. Pour plus d'informations sur la restauration ou le recyclage d'un document dans SharePoint, consultez [Planifier la protection du contenu à l’aide de corbeilles et du contrôle de version](https://go.microsoft.com/fwlink/?LinkId=238669).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Vue d'ensemble de la mise à niveau des classeurs](#bkmk_overview)  
  
-   [Mettre à niveau des classeurs SQL Server 2008 R2 vers des classeurs SQL Server 2012 Service Pack 1 (SP1)](#bkmk_to_2012sp1_from_2008r2)  
  
-   [Mise à niveau vers des classeurs Office 2013 à partir de versions créées à l'aide du complément PowerPivot 2012 pour Excel](#bkmk_to_2012sp1_from_2012)  
  
-   [Mise à niveau vers des classeurs SQL Server 2012 à partir de versions créées à l'aide du complément PowerPivot 2008 R2 pour Excel 2010](#bkmk_to_2012_from_2008R2)  
  
-   [Exécution de plusieurs versions de classeurs sur un serveur plus récent](#bkmk_runold)  
  
##  <a name="overview-of-upgrading-workbooks"></a><a name="bkmk_overview"></a>Vue d’ensemble de la mise à niveau des classeurs  
 Un classeur PowerPivot est un classeur Excel qui contient des données PowerPivot incorporées. La mise à niveau d'un classeur présente deux avantages :  
  
-   Utilisez les nouvelles fonctionnalités de [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)].  
  
-   Permet l'actualisation planifiée des données pour les classeurs exécutés avec un serveur [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services en mode SharePoint.  
  
> [!IMPORTANT]  
>  Vous ne pouvez pas restaurer un classeur mis à niveau : assurez-vous de faire une copie du fichier si vous souhaitez l'utiliser dans la version antérieure de [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], ou dans une version antérieure de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].  
  
 Le tableau suivant répertorie la prise en charge et le comportement des classeurs PowerPivot sur l'environnement dans lequel le classeur a été créé. Le comportement décrit inclut l'expérience 'utilisateur générale, les options de mise à niveau prises en charge pour mettre à niveau le classeur vers un environnement spécifique, et le comportement de l'actualisation planifiée des données d'un classeur qui n'a pas encore été mis à niveau.  
  
### <a name="workbook-behavior-and-upgrade-options"></a>Comportement et options de mise à niveau des classeurs  
  
|Environnement de création|\<|Prise en charge et comportement|>|  
|----------------|--------|--------------------------|--------|  
||**2008 R2 PowerPivot pour SharePoint 2010**|**2012 PowerPivot pour SharePoint 2010**|**2012 SP1 PowerPivot pour SharePoint 2013**|  
|**2008 R2 PowerPivot pour Excel 2010**|Toutes les fonctionnalités|**Expérience :** les utilisateurs peuvent interagir avec le classeur dans le navigateur et l'utiliser comme source de données pour d'autres solutions.<br /><br /> **Mise à niveau :** les classeurs sont mis à niveau automatiquement dans la bibliothèque de documents si la mise à niveau automatique est activée pour le service système PowerPivot dans la batterie de serveurs SharePoint.<br /><br /> **Planification de l'actualisation des données :** NON prise en charge. Le classeur doit être mis à niveau.|**Expérience :** les utilisateurs peuvent interagir avec le classeur et l'utiliser comme source de données pour d'autres solutions.<br /><br /> **Mise à niveau :** la mise à niveau automatique n'est pas disponible. Les utilisateurs doivent mettre à niveau leurs classeurs 2008 R2 vers la version 2012 ou version Office 2013 manuellement.<br /><br /> **Planification de l'actualisation des données :** NON prise en charge. Le classeur doit être mis à niveau.|  
|**2012 PowerPivot pour Excel**|Non pris en charge|Toutes les fonctionnalités|**Expérience :** les utilisateurs peuvent interagir avec le classeur dans le navigateur et l'utiliser comme source de données pour d'autres solutions. La planification de l'actualisation des données est disponible.<br /><br /> **Mise à niveau :** la mise à niveau automatique n'est pas prise en charge. Les utilisateurs peuvent mettre à niveau leurs classeurs vers la version Office 2013.<br /><br /> **Planification de l'actualisation des données :** prise en charge.|  
|**Excel 2013**|Non pris en charge|Non pris en charge|Toutes les fonctionnalités|  
  
##  <a name="upgrade-to-sql-server-2012-service-pack-1-sp1-workbooks-from-2008-r2-workbooks"></a><a name="bkmk_to_2012sp1_from_2008r2"></a>Mettre à niveau vers SQL Server classeurs 2012 Service Pack 1 (SP1) à partir de classeurs 2008 R2  
 Cette section décrit la mise à niveau de classeurs SQL Server 2008 R2 PowerPivot pour Excel 2010 vers des classeurs SQL Server 2012 SP1 PowerPivot pour Excel 2013.  
  
 **Modification du comportement :** les classeurs PowerPivot SQL Server 2008 R2 ne sont pas mis à niveau automatiquement lorsqu'ils sont utilisés dans SQL Server 2012 SP1 PowerPivot pour SharePoint 2013. Par conséquent, les actualisations planifiées de données ne fonctionnent pas pour les classeurs PowerPivot SQL Server 2008 R2.  
  
 Les classeurs SQL Server 2008 R2 s'ouvrent dans PowerPivot pour SharePoint 2013, cependant les actualisations planifiées de données ne fonctionnent pas. Si vous observez l'historique d'actualisation, vous pouvez voir un message d'erreur semblable au message suivant :  
  
 «Le classeur contient un modèle PowerPivot non pris en charge. Le modèle PowerPivot dans le classeur est au format SQL Server 2008 R2 PowerPivot pour Excel 2010. Les modèles PowerPivot pris en charge sont les suivants :  
  
-   SQL Server 2012 PowerPivot pour Excel 2010.  
  
-   SQL Server 2012 PowerPivot pour Excel 2013.  
  
 **Comment mettre à niveau un classeur :** l'actualisation planifiée de données ne fonctionne pas tant que vous n'avez pas mis à niveau le classeur vers un classeur 2012. Pour mettre à niveau le classeur et le modèle qu'il contient, procédez de l'une des façons suivantes :  
  
-   Téléchargez et ouvrez le classeur dans Microsoft Excel 2010 avec le complément SQL Server 2012 PowerPivot pour Excel installé.  
  
     Ouvrez la fenêtre PowerPivot et mettez à niveau le modèle PowerPivot.  
  
     Ensuite, enregistrez le classeur et republiez-le sur SharePoint.  
  
-   Téléchargez et ouvrez le classeur dans Microsoft Excel 2013.  
  
     Ouvrez la fenêtre PowerPivot et mettez à niveau le modèle PowerPivot.  
  
     Ensuite, enregistrez le classeur et republiez-le sur le serveur SharePoint.  
  
 Pour plus d’informations sur les modifications apportées aux fonctionnalités de Analysis Services, consultez [changements de comportement apportés aux fonctionnalités de Analysis Services dans SQL Server 2014](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)  
  
 Pour plus d’informations sur l’historique d’actualisation, consultez [afficher l’historique d’actualisation des données &#40;PowerPivot pour SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).  
  
##  <a name="upgrade-to-office-2013-workbooks-from-versions-created-by-using-the-2012-powerpivot-add-in-for-excel"></a><a name="bkmk_to_2012sp1_from_2012"></a>Effectuer une mise à niveau vers des classeurs Office 2013 à partir de versions créées à l’aide du complément PowerPivot 2012 pour Excel  
 Cette section décrit la mise à niveau **de** classeurs SQL Server 2012 PowerPivot pour Excel 2010 **vers** SQL Server 2012 SP1 PowerPivot pour Excel 2013.  
  
 La mise à niveau d'un classeur résout l'erreur suivante qui se produit lors de la tentative d'actualisation planifiée des données sur le classeur de version précédente :  
  
 « L’opération d’actualisation des classeurs créés avec une version antérieure de PowerPivot n’est pas disponible ».  
  
 **Procédure de mise à niveau d'un classeur**  
  
1.  Mettez à niveau chaque classeur manuellement en l'ouvrant dans Microsoft Excel 2013.  
  
2.  Pour mettre à niveau le classeur et le modèle qu'il contient, téléchargez et ouvrez le classeur dans Microsoft Excel 2013.  
  
3.  Ouvrez la fenêtre PowerPivot et mettez à niveau le modèle PowerPivot.  
  
4.  Ensuite, enregistrez le classeur et republiez-le sur le serveur SharePoint 2013.  
  
##  <a name="upgrade-to-sql-server-2012-workbooks-from-versions-created-by-using-the-2008-r2-powerpivot-add-in-for-excel-2010"></a><a name="bkmk_to_2012_from_2008R2"></a>Effectuer une mise à niveau vers des classeurs SQL Server 2012 à partir de versions créées à l’aide du complément PowerPivot 2008 R2 pour Excel 2010  
 Cette section décrit la mise à niveau de classeurs **de** SQL Server 2008 R2 PowerPivot pour Excel 2010 **vers** SQL Server 2012 PowerPivot pour Excel 2010.  
  
 La mise à niveau d'un classeur résout l'erreur suivante qui se produit lors de la tentative d'actualisation planifiée des données sur le classeur de version précédente :  
  
 « L’opération d’actualisation des classeurs créés avec une version antérieure de PowerPivot n’est pas disponible ».  
  
 **Procédure de mise à niveau d'un classeur**  
  
 Vous pouvez effectuer la mise à niveau de deux façons :  
  
1.  Mettez à niveau chaque classeur manuellement en l'ouvrant dans Excel sur un ordinateur doté de la version [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] de PowerPivot pour Excel, puis republiez-le sur le serveur. Lorsque vous ouvrez le classeur dans une version plus récente du complément, les opérations internes suivantes se produisent : le fournisseur de données dans la chaîne de connexion de données du classeur est mis à jour vers MSOLAP.5, les métadonnées sont mises à jour et les relations sont recréées pour assurer la conformité avec une implémentation plus récente.  
  
2.  Sinon, un administrateur SharePoint peut activer la fonctionnalité de mise à niveau automatique pour le service système PowerPivot dans une batterie de serveur SharePoint pour mettre à niveau automatiquement un classeur [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot lorsque l'actualisation planifiée des données s'exécute (seuls les classeurs configurés pour une actualisation planifiée des données sont mis à niveau).  
  
    > [!NOTE]  
    >  La mise à niveau automatique est une fonctionnalité de configuration de serveur ; vous ne pouvez pas l'activer ou la désactiver pour des classeurs, des bibliothèques ou les collections de sites spécifiques.  
  
 **Procédure de configuration de la mise à niveau automatique lors de l'actualisation des données**  
  
 Pour utiliser la mise à niveau automatique, vous devez activer la case à cocher **Mettre automatiquement à niveau les classeurs PowerPivot pour permettre l'actualisation des données à partir du serveur** dans l'outil de configuration PowerPivot. Dans l'outil, la case à cocher se trouve dans la page **Mettre à niveau le service système PowerPivot** , et dans la page **Créer une application de service PowerPivot** si vous configurez une nouvelle installation.  
  
 Vous pouvez exécuter l'applet de commande suivante pour vérifier si la mise à niveau automatique est activée :  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 La sortie de la commande Get-PowerPivotSystemService est une liste de propriétés et de valeurs correspondantes. Vous devriez voir `WorkbookUpgradeOnDataRefresh` dans la liste des propriétés. Elle aura la valeur **true** si la mise à niveau automatique est activée. Si elle a la valeur **false**, passez à l'étape suivante, pour activer la mise à niveau automatique des classeurs.  
  
 Pour activer la mise à niveau automatique des classeurs, exécutez la commande suivante :  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true -Confirm:$false  
```  
  
 Après la mise à niveau du classeur, vous pouvez utiliser l'actualisation planifiée des données et les nouvelles fonctionnalités du complément PowerPivot pour Excel.  
  
##  <a name="running-multiple-workbook-versions-on-a-newer-server"></a><a name="bkmk_runold"></a> Exécution de plusieurs versions de classeurs sur un serveur plus récent  
 Vous pouvez exécuter les versions antérieures et les versions plus récentes des classeurs PowerPivot côte à côte sur une instance [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].  
  
 Selon la façon dont vous avez installé le serveur, **vous devrez peut-être** installer une version antérieure du fournisseur OLE DB Analysis Services avant de pouvoir accéder aux classeurs plus anciens et plus récents sur le même serveur.  
  
 Notez que la publication de classeurs de version plus récente sur des instances SQL Server antérieures de [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] n'est pas prise en charge. Une instance de [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ne charge pas un classeur créé dans la version [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] de [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], et une instance de SQL Server 2012 ne charge pas les classeurs Office 2013 avec des modèles de données avancés que vous avez créés à l'aide de la version [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] de PowerPivot dans Excel.  
  
###  <a name="how-to-check-for-msolap-data-provider-information-in-a-powerpivot-workbook"></a><a name="bkmk_msolapxslx"></a>Comment rechercher des informations de Fournisseur de données MSOLAP dans un classeur PowerPivot  
 Suivez les instructions suivantes pour vérifier le fournisseur OLE DB utilisé dans un classeur PowerPivot. La vérification des informations de connexion de données ne nécessite pas l'installation du complément [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] .  
  
1.  Dans Excel, dans l'onglet Données, cliquez sur **Connexions**. Cliquez sur **Propriétés**.  
  
2.  Dans l'onglet **Définition** , la version du fournisseur apparaît au début de la chaîne de connexion.  
  
     **Provider=MSOLAP.5** indique qu’il s’agit d’un classeur [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
     **Provider=MSOLAP.4** indique [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].  
  
     **Data Source=$Embedded$** indique que le classeur est un classeur PowerPivot qui utilise une base de données incorporée.  
  
###  <a name="how-to-check-for-the-current-version-of-the-msolap-data-provider-on-a-local-computer"></a><a name="bkmk_msolappc"></a> Comment vérifier la version actuelle du fournisseur de données MSOLAP sur un ordinateur local  
 Suivez les instructions suivantes pour vérifier quelle est la version actuelle du fournisseur OLE DB sur le serveur ou la station de travail qui exécute des classeurs PowerPivot. Connaître la version actuelle peut vous aider à dépanner des erreurs de connexion de données après la mise à niveau.  
  
1.  Dans l'Éditeur du Registre, allez à HKEY_CLASSES_ROOT  
  
2.  Faites défiler jusqu'à MSOLAP. Vérifiez que MSOLAP.5 apparaît parmi les fournisseurs OLAP installés sur le système. Vérifiez que MSOLAP | CurVer est défini sur MSOLAP.5  
  
## <a name="see-also"></a>Voir aussi  
 [Migrer PowerPivot vers SharePoint 2013](migrate-power-pivot-to-sharepoint-2013.md)   
 [Mettre à niveau PowerPivot pour SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Nouveautés de Analysis Services et Business Intelligence](../../what-s-new-in-analysis-services.md)   
 [Afficher l’historique d’actualisation des données &#40;PowerPivot pour SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
