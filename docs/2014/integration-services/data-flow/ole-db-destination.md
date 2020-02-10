---
title: Destination OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdest.f1
helpviewer_keywords:
- fast-load data access mode [Integration Services]
- OLE DB destination [Integration Services]
- fast load options [Integration Services]
- fast-load options [Integration Services]
- destinations [Integration Services], OLE DB
- fast load data access mode [Integration Services]
- inserting data
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d9b75cc79f1f127858ce8547aa222524614ac09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62901483"
---
# <a name="ole-db-destination"></a>Destination OLE DB
  La destination OLE DB charge des données dans différentes bases de données compatibles OLE DB à l'aide d'une table ou d'une vue de base de données ou d'une commande SQL. Par exemple, la source OLE DB peut charger des données dans des tables de bases de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La destination OLE DB propose cinq modes d'accès différents pour charger les données :  
  
-   Une table ou une vue. Vous pouvez indiquer une table ou une vue existante, ou créer une table ;  
  
-   une table ou une vue et des options de chargement rapide. Vous pouvez indiquer une table existante ou en créer une ;  
  
-   Une table ou une vue spécifiée dans une variable.  
  
-   une table ou une vue spécifiée dans une variable et des options de chargement rapide ;  
  
-   Les résultats d'une instruction SQL.  
  
> [!NOTE]  
>  La destination OLE DB ne prend pas en charge les paramètres. Si vous devez exécuter une instruction INSERT paramétrable, envisagez d'utiliser la transformation de commande OLE DB. Pour plus d’informations, voir [OLE DB Command Transformation](transformations/ole-db-command-transformation.md).  
  
 Lorsque la destination OLE DB charge des données qui utilisent un jeu de caractères codés sur deux octets (DBCS), les données risquent d'être endommagées si le mode d'accès aux données n'utilise pas l'option de chargement rapide et si le gestionnaire de connexions OLE DB utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB). Pour garantir l’intégrité des données DBCS, vous devez configurer le gestionnaire de connexions OLE DB pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ou l’un des modes d’accès avec chargement rapide : **Table ou vue - chargement rapide** ou **Variable de nom de table ou de vue - chargement rapide**. Ces deux options sont disponibles dans la boîte de dialogue **Éditeur de destination OLE DB** . Quand vous programmez le [!INCLUDE[ssIS](../../includes/ssis-md.md)] modèle objet, vous devez définir la propriété `OpenRowset Using FastLoad`AccessMode sur `OpenRowset Using FastLoad From Variable`, ou.  
  
> [!NOTE]  
>  Si vous utilisez la boîte de dialogue **Éditeur de destination OLE DB** dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour créer la table de destination dans laquelle la destination OLE DB insère des données, vous devrez peut-être sélectionner la table que vous venez de créer manuellement. La sélection manuelle est nécessaire lorsqu'un fournisseur OLE DB tel que le fournisseur OLE DB pour DB2, ajoute manuellement des identificateurs de schéma au nom de la table.  
  
> [!NOTE]  
>  L'instruction CREATE TABLE que la boîte de dialogue **Éditeur de destination OLE DB** génère peut nécessiter une modification selon le type de destination. Par exemple, certaines destinations ne prennent pas en charge les types de données que l'instruction CREATE TABLE utilise.  
  
 Cette destination utilise un gestionnaire de connexions OLE DB pour se connecter à une source de données et le gestionnaire de connexions indique le fournisseur OLE DB à utiliser. Pour plus d’informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
 Un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contient également l'objet de source de données à partir duquel vous pouvez créer un gestionnaire de connexions OLE DB afin de rendre les sources de données et les vues de sources de données disponibles pour la destination OLE DB.  
  
 Une destination OLE DB inclut des mappages entre les colonnes d'entrée et les colonnes de la source de données de destination. Vous n'avez pas besoin de mapper les colonnes d'entrée à toutes les colonnes de destination, mais en fonction des propriétés des colonnes de destination, des erreurs peuvent se produire si aucune colonne d'entrée n'est mappée aux colonnes de destination. Par exemple, si une colonne de destination n'autorise pas les valeurs null, une colonne d'entrée doit être mappée à cette colonne. Par ailleurs, les types de données des colonnes mappées doivent être compatibles. Par exemple, vous ne pouvez pas mapper une colonne d'entrée avec un type de données string à une colonne de destination avec un type de données numeric.  
  
 La destination OLE DB comporte une entrée normale et une sortie d'erreur.  
  
 Pour plus d'informations sur les types de données, consultez [Integration Services Data Types](integration-services-data-types.md).  
  
## <a name="fast-load-options"></a>Options de chargement rapide  
 Si la destination OLE DB utilise un mode d’accès aux données par chargement rapide, vous pouvez spécifier les options de chargement rapide dans l’interface utilisateur, **Éditeur de destination OLE DB**, pour la destination :  
  
-   Conserver les valeurs d'identité du fichier de données importé ou utiliser les valeurs uniques affectées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Conserver une valeur null pendant l'opération de chargement en masse.  
  
-   Vérifier les contraintes sur la table ou la vue cible au cours de l'opération d'importation en masse.  
  
-   Acquisition d'un verrou au niveau de la table pour la durée de l'opération de chargement en masse.  
  
-   Spécifier le nombre de lignes dans le traitement et la taille de validation.  
  
 Certaines options de chargement rapide sont stockées dans des propriétés spécifiques de la destination OLE DB. Par exemple, FastLoadKeepIdentity spécifie s’il convient de conserver des valeurs d’identification, FastLoadKeepNulls précise s’il faut conserver des valeurs NULL et FastLoadMaxInsertCommitSize spécifie le nombre de lignes à valider en tant que traitement. D’autres options de chargement rapide sont stockées dans une liste séparée par des virgules dans la propriété FastLoadOptions. Si la destination OLE DB utilise toutes les options de chargement rapide stockées dans FastLoadOptions et répertoriées dans la boîte de dialogue **éditeur de destination OLE DB** , la valeur de la propriété est `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000`définie sur. La valeur 1 000 indique que la destination est configurée pour utiliser des traitements de 1 000 lignes.  
  
> [!NOTE]  
>  Tout échec de contrainte à la destination entraîne l’échec de la totalité du lot de lignes définies par FastLoadMaxInsertCommitSize.  
  
 Outre les options de chargement rapide dévoilées dans la boîte de dialogue **Éditeur de destination OLE DB** , vous pouvez configurer la destination OLE DB afin d’utiliser les options de chargement en masse suivantes en tapant les options dans la propriété FastLoadOptions, dans la boîte de dialogue **Éditeur avancé** .  
  
|Option de chargement rapide|Description|  
|----------------------|-----------------|  
|KILOBYTES_PER_BATCH|Indique la taille à insérer en kilo-octets. L’option a la forme `KILOBYTES_PER_BATCH`  =  \<d’une valeur**>** entière positive.|  
|FIRE_TRIGGERS|Spécifie si des déclencheurs sont activés sur la table d'insertion. L’option a la forme **FIRE_TRIGGERS**. La présence de l'option indique que des déclencheurs sont activés.|  
|ORDER|Spécifie comment les données d'entrée sont triées. L’option a la forme ORDER \<nom de colonne> ASC&#124;DESC. Il n'y a pas de limite quant au nombre de colonnes indiquées et la spécification de l'ordre de tri est facultative. Si l'ordre de tri est omis, l'opération d'insertion part du principe que les données ne sont pas triées.<br /><br /> Remarque : les performances peuvent être améliorées si vous utilisez l’option ORDER pour trier les données d’entrée selon l’index cluster de la table.|  
  
 Les mots clés [!INCLUDE[tsql](../../includes/tsql-md.md)] sont traditionnellement tapés en majuscules, mais ils ne tiennent pas compte de la casse.  
  
 Pour en savoir plus sur les options de chargement rapide, consultez [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
## <a name="troubleshooting-the-ole-db-destination"></a>Résolution des problèmes liés à la destination OLE DB  
 Vous pouvez consigner les appels que la destination OLE DB effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés à l'enregistrement de données vers des sources de données externes que réalise la destination OLE DB. Pour consigner les appels que la destination OLE DB effectue vers des fournisseurs de données externes, activez la journalisation de package et sélectionnez l'événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuring-the-ole-db-destination"></a>Configuration de la destination OLE DB  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination OLE DB** , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de destination de OLE DB &#40;page Gestionnaire de connexions&#41;](../ole-db-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de OLE DB &#40;page Mappages&#41;](../ole-db-destination-editor-mappings-page.md)  
  
-   [OLE DB éditeur de destination &#40;page sortie d’erreur&#41;](../ole-db-destination-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées OLE DB](ole-db-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Charger des données à l'aide de la destination OLE DB](ole-db-destination.md)  
  
-   [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Source OLE DB](ole-db-source.md)  
  
 [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md)  
  
 [Flux de données](data-flow.md)  
  
  
