---
title: Destination SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 818f78cd0b38aba0a7201eb28f49eb573ba32672
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770679"
---
# <a name="sql-server-destination"></a>Destination SQL Server
  La destination SQL Server se connecte à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale et charge en masse des données dans des tables et des vues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous ne pouvez pas utiliser la destination SQL Server dans des packages ayant accès à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur distant. Les packages doivent plutôt utiliser la destination OLE DB. Pour plus d’informations, consultez [OLE DB Destination](ole-db-destination.md).  
  
## <a name="permissions"></a>Autorisations  
 Les utilisateurs qui exécutent des packages incluant la destination SQL Server nécessitent l'autorisation « Create global objects » (Créer des objets globaux). Vous pouvez attribuer cette autorisation aux utilisateurs à l’aide de l’outil Stratégie de sécurité locale accessible dans le menu **Outils d’administration** . Si vous recevez un message d'erreur lors de l'exécution d'un package qui utilise la destination SQL Server, assurez-vous que le compte exécutant le package a l'autorisation « Create global objects » (Créer des objets globaux).  
  
## <a name="bulk-inserts"></a>Insertions en bloc  
 Si vous essayez d’utiliser la destination SQL Server en bloc des données de charge dans une base de données SQL Server distante, vous pouvez voir un message d’erreur semblable au suivant : « Un enregistrement OLE DB est disponible. Source : « Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client » Hresult : 0x80040E14 description : « Impossible chargement en masse, car l’objet de mappage de fichier SSIS 'Global\DTSQLIMPORT' n’a pas pu être ouvert. Code d'erreur du système d'exploitation 2 (Le système ne trouve pas le fichier spécifié.). Vérifiez que vous accédez à un serveur local par le biais de la sécurité Windows." »  
  
 La destination SQL Server offre la même insertion rapide de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que la tâche d’insertion en bloc ; toutefois, l’utilisation d’une destination SQL Server permet à un package d’appliquer des transformations à des données de colonne avant que les données ne soient chargées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour le chargement de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], envisagez l'utilisation de la destination SQL Server plutôt que la destination OLE DB.  
  
### <a name="bulk-insert-options"></a>Options d'insertion en bloc  
 Si la destination SQL Server utilise un mode d'accès aux données par chargement rapide, vous pouvez spécifier les options de chargement rapide suivantes :  
  
-   Conservation des valeurs d'identité du fichier de données importé ou utilisation de valeurs uniques assignées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Conservation des valeurs nulles durant l'opération de chargement en masse.  
  
-   Vérification des contraintes sur la table ou la vue cible durant l'opération d'importation en bloc.  
  
-   Acquisition d'un verrou au niveau de la table pour la durée de l'opération de chargement en masse.  
  
-   Exécution de déclencheurs d'insertion définis sur la table de destination durant l'opération de chargement en masse.  
  
-   Spécification du numéro de la première ligne de l'entrée à charger durant l'opération d'insertion en bloc.  
  
-   Spécification du numéro de la dernière ligne de l'entrée à charger durant l'opération d'insertion en bloc.  
  
-   Spécification du nombre maximal d'erreurs tolérées avant l'annulation de l'opération de chargement en masse. Chaque ligne ne pouvant pas être importée est comptée comme une erreur.  
  
-   Spécification des colonnes de l'entrée qui contiennent des données triées.  
  
 Pour plus d’informations sur les options de chargement en masse, consultez [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
#### <a name="performance-improvements"></a>Optimisation des performances  
 Pour améliorer les performances d'une insertion en bloc et l'accès aux données de table durant l'opération d'insertion en bloc, vous devez modifier les options par défaut comme suit :  
  
-   Ne pas vérifier les contraintes sur la table ou la vue cible durant l'opération d'importation en bloc.  
  
-   Ne pas exécuter de déclencheurs d'insertion définis sur la table de destination durant l'opération de chargement en masse.  
  
-   Ne pas appliquer de verrou sur la table. De cette manière, la table reste disponible pour les autres utilisateurs et applications durant l'opération d'insertion en bloc.  
  
## <a name="configuration-of-the-sql-server-destination"></a>Configuration de la destination SQL Server  
 Vous pouvez configurer la destination SQL Server de plusieurs manières :  
  
-   Spécifiez la table ou la vue dans laquelle charger les données en masse.  
  
-   Personnalisez l'opération de chargement en masse en spécifiant des options telles que la vérification des contraintes.  
  
-   Indiquez si toutes les lignes doivent être validées en un seul traitement ou définissez le nombre maximum de lignes à valider en tant que traitement.  
  
-   Spécifiez un délai d'expiration pour l'opération de chargement en masse.  
  
 Cette destination utilise un gestionnaire de connexions OLE DB pour se connecter à une source de données et le gestionnaire de connexions spécifie le fournisseur OLE DB à utiliser. Pour plus d’informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
 Un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit également l'objet de source de données à partir duquel vous pouvez créer un gestionnaire de connexions OLE DB. Les sources de données et les vues de sources de données sont ainsi disponibles pour la destination SQL Server.  
  
 La destination SQL Server possède une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination SQL**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination SQL &#40;page Gestionnaire de connexions&#41;](../sql-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination SQL &#40;page Mappages&#41;](../sql-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination SQL &#40;page Avancé&#41;](../sql-destination-editor-advanced-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées de la destination SQL Server](sql-server-destination-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Charger des données en masse à l’aide de la destination SQL Server](sql-server-destination.md)  
  
-   [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Charger des données en masse à l'aide de la destination SQL Server](sql-server-destination.md)  
  
-   [Définir les propriétés d'un composant de flux de données](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=199482)(Vous pouvez obtenir l’erreur « Impossible de préparer l’insertion en bloc SSIS pour l’insertion de données »sur les systèmes UAC), sur support.microsoft.com.  
  
-   Article technique, [Guide des performances de chargement des données](https://go.microsoft.com/fwlink/?LinkId=233700), sur le site msdn.microsoft.com.  
  
-   Article technique, [Utilisation de SQL Server Integration Services pour le chargement en masse des données](https://go.microsoft.com/fwlink/?LinkId=233701), sur le site simple-talk.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](data-flow.md)  
  
  
