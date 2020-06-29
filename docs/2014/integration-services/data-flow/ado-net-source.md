---
title: Source ADO NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ad603915ae20c7959a5cd74e441135f88fd3ebfc
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432476"
---
# <a name="ado-net-source"></a>Source ADO NET
  La source ADO .NET exploite des données issues d'un fournisseur .NET et les met à la disposition du flux de données.  
  
 Vous pouvez utiliser la source ADO .NET. pour vous connecter à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. La connexion à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] via OLE DB n'est pas prise en charge. Pour plus d’informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)], consultez [Recommandations générales et limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="data-type-support"></a>Prise en charge du type de données  
 La source convertit tout type de données qui ne mappe pas à un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] spécifique en un type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DT_NTEXT. Cette conversion se produit même si le type de données est `System.Object`.  
  
 Vous pouvez remplacer le type de données DT_NTEXT par le type de données DT_WSTR, et inversement. Pour modifier les types de données, définissez la propriété **DataType** dans la boîte de dialogue **Éditeur avancé** de la source ADO .NET. Pour plus d’informations, consultez [Propriétés communes](../common-properties.md).  
  
 Le type de données DT_NTEXT peut également être converti en type de données DT_BYTES ou DT_STR en utilisant une transformation de conversion de données après la source ADO .NET. Pour plus d’informations, voir [Data Conversion Transformation](transformations/data-conversion-transformation.md).  
  
 Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], les types de données de date, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2 et DT_DBTIMESTAMPOFFSET, mappent à certains types de données de date de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez configurer la source ADO .NET pour convertir les types de données de date utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en types de données de date utilisés par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour configurer la source ADO .NET pour convertir ces types de données de date, affectez à la propriété **Type System Version** du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] la valeur **Dernière**. (La propriété **Type System Version** se trouve dans la page **Tous** de la boîte de dialogue **Gestionnaire de connexions** . Pour ouvrir la boîte de dialogue **Gestionnaire de connexions** , cliquez avec le bouton droit sur le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , puis cliquez sur **Modifier**.)  
  
> [!NOTE]  
>  Si la propriété **Type System Version** du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] a la valeur **SQL Server 2005**, le système convertit les types de données de date [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en DT_WSTR.  
  
 Le système convertit les types de données définis par l’utilisateur (UDT) en objets blob (Binary Large Object) [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] quand le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] spécifie le fournisseur en tant que fournisseur de données .NET pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient). Le système applique les règles suivantes quand il convertit le type de données UDT :  
  
-   Si les données sont un UDT non volumineux, le système convertit les données en DT_BYTES.  
  
-   Si les données sont un type UDT non volumineux et que la propriété **Length** de la colonne sur la base de données a la valeur -1 ou une valeur supérieure à 8 000 octets, le système convertit les données en DT_IMAGE.  
  
-   Si les données sont un UDT volumineux, le système convertit les données en DT_IMAGE.  
  
    > [!NOTE]  
    >  Si la source ADO .NET n'est pas configurée pour utiliser la sortie d'erreur, le système transmet les données à la colonne DT_IMAGE par segments de 8 000 octets. Si la source ADO .NET est configurée pour utiliser la sortie d'erreur, le système passe la totalité du tableau d'octets à la colonne DT_IMAGE. Pour plus d’informations sur la configuration des composants pour utiliser la sortie d’erreur, consultez [Gestion des erreurs dans les données](error-handling-in-data.md).  
  
 Pour plus d’informations sur les types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , les conversions de types de données prises en charge et le mappage de types de données entre certaines bases de données incluant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Types de données d’Integration Services](integration-services-data-types.md).  
  
 Pour plus d’informations sur le mappage entre les types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les types de données managés, consultez [Utilisation de types de données dans le flux de données](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).  
  
## <a name="ado-net-source-troubleshooting"></a>Résolution des problèmes liés à la source ADO .NET  
 Vous pouvez consigner les appels que la source ADO .NET effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés au chargement de données qu'effectue la source ADO .NET à partir de sources de données externes. Pour consigner les appels que la source ADO .NET effectue vers des fournisseurs de données externes, activez la journalisation de package et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="ado-net-source-configuration"></a>Configuration de la source ADO .NET  
 Vous configurez la source ADO .NET en fournissant l'instruction SQL qui définit le jeu de résultats. Par exemple, une source ADO .NET qui se connecte à la base de données [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] et utilise l’instruction SQL `SELECT * FROM Production.Product` extrait toutes les lignes de la table **Production.Product** et fournit le dataset à un composant en aval.  
  
> [!NOTE]  
>  Lorsque vous utilisez une instruction SQL pour appeler une procédure stockée qui retourne des résultats à partir d'une table temporaire, utilisez l'option WITH RESULT SETS afin de définir les métadonnées du jeu de résultats.  
  
> [!NOTE]  
>  Si vous utilisez une instruction SQL pour exécuter une procédure stockées et que le package échoue avec l'erreur suivante, vous pouvez résoudre l'erreur en ajoutant l'instruction `SET FMTONLY OFF` avant l'instruction exec.  
>   
>  **La colonne « nom_colonne » est introuvable dans la source de données.**  
  
 La source ADO .NET utilise un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] pour se connecter à une source de données, et le gestionnaire de connexions spécifie le fournisseur .NET. Pour plus d’informations, consultez [Gestionnaire de connexions ADO.NET](../connection-manager/ado-net-connection-manager.md).  
  
 La source ADO .NET a une sortie normale et une sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées ADO NET](ado-net-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir les propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Destination DataReader](datareader-destination.md)   
 [Destination ADO NET](ado-net-destination.md)   
 [Flux de données](data-flow.md)  
  
  
