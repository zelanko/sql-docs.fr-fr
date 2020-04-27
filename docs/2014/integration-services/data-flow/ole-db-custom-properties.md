---
title: Propriétés personnalisées OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 13a82d41-dd7a-4708-bc84-4407a536c877
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 996acc5f8e9b47af683c8d8376515f7f59e63120
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62770989"
---
# <a name="ole-db-custom-properties"></a>Propriétés personnalisées OLE DB
  **Propriétés personnalisées des sources**  
  
 La source OLE DB comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source OLE DB. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|Mode utilisé pour accéder à la base de données. Les valeurs possibles sont **Open Rowset**, **Open Rowset de la variable**, `SQL Command`et la **commande SQL à partir d’une variable**. La valeur par défaut est **Open Rowset**.|  
|AlwaysUseDefaultCodePage|Boolean|Valeur qui indique s'il faut utiliser la valeur de la propriété `DefaultCodePage` pour chaque colonne ou tenter de dériver la page de codes à partir des paramètres régionaux de chaque colonne. La valeur par défaut de cette propriété est `False`.|  
|CommandTimeout|Integer|Nombre de secondes accordées comme délai d'exécution d'une commande. Une valeur égale à 0 indique un délai illimité.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source OLE DB**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|DefaultCodePage|Integer|Page de codes à utiliser lorsque les informations de page de codes ne sont pas disponibles depuis la source de données.|  
|OpenRowset|String|Nom de l'objet de base de données utilisé pour ouvrir un ensemble de lignes.|  
|OpenRowsetVariable|String|Variable qui contient le nom de l'objet de base de données utilisé pour ouvrir un ensemble de lignes.|  
|ParameterMapping|String|Mappage des paramètres de la commande SQL en variables.|  
|SqlCommand|String|Commande SQL à exécuter.|  
|SqlCommandVariable|String|Variable qui contient la commande SQL à exécuter.|  
  
 La sortie et les colonnes de sortie de la source OLE DB ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [OLE DB Source](ole-db-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination OLE DB comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination OLE DB. Toutes les propriétés sont en lecture/écriture.  
  
> [!NOTE]  
>  Les options FastLoad répertoriées ici (FastLoadKeepIdentity, FastLoadKeepNulls et FastLoadOptions) correspondent aux propriétés qui portent des noms similaires et sont présentées dans l'interface `IRowsetFastLoad` implémentée par le fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB). Pour plus d'informations, effectuez une recherche sur IRowsetFastLoad dans MSDN Library.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Valeur qui spécifie la manière dont la destination accède à sa base de données de destination.<br /><br /> Cette propriété peut prendre les valeurs suivantes :<br /><br /> `OpenRowset`(0) : vous fournissez le nom d’une table ou d’une vue.<br />`OpenRowset from Variable`(1) : vous fournissez le nom d’une variable qui contient le nom d’une table ou d’une vue.<br />`OpenRowset Using Fastload`(3) : vous fournissez le nom d’une table ou d’une vue.<br />`OpenRowset Using Fastload from Variable`(4) : vous fournissez le nom d’une variable qui contient le nom d’une table ou d’une vue.<br />`SQL Command`(2) : vous fournissez une instruction SQL.|  
|AlwaysUseDefaultCodePage|Boolean|Valeur qui indique s'il faut utiliser la valeur de la propriété `DefaultCodePage` pour chaque colonne ou tenter de dériver la page de codes à partir des paramètres régionaux de chaque colonne. La valeur par défaut de cette propriété est `False`.|  
|CommandTimeout|Integer|Nombre maximal de secondes pendant lesquelles la commande SQL peut être exécutée avant d'arriver à expiration. La valeur 0 indique un délai infini. La valeur par défaut de cette propriété est 0.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de destination OLE DB**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|DefaultCodePage|Integer|Page de codes par défaut associée à la destination OLE DB.|  
|FastLoadKeepIdentity|Boolean|Valeur spécifiant si les valeurs d'identité doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement avec l'une des options de chargement rapide. La valeur par défaut de cette propriété est `False`. Cette propriété correspond à la `SSPROP_FASTLOADKEEPIDENTITY`propriété [&#41;OLE DB IRowsetFastLoad &#40;OLE DB](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) .|  
|FastLoadKeepNulls|Boolean|Valeur spécifiant si les valeurs NULL doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement avec l'une des options de chargement rapide. La valeur par défaut de cette propriété est `False`. Cette propriété correspond à la `SSPROP_FASTLOADKEEPNULLS`propriété [&#41;OLE DB IRowsetFastLoad &#40;OLE DB](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) .|  
|FastLoadMaxInsertCommitSize|Integer|Valeur qui spécifie la taille du lot que la destination OLE DB tente de valider au cours des opérations de chargement rapide. La valeur par défaut ( **0**) indique une opération de validation simple après le traitement de toutes les lignes.|  
|FastLoadOptions|String|Collection d'options de chargement rapide. Les options de chargement rapide incluent le verrouillage des tables et la vérification des contraintes. Vous pouvez spécifier une de ces options, les deux ou ni l'une ni l'autre. Cette propriété correspond à la OLE DB propriété `SSPROP_FASTLOADOPTIONS` IRowsetFastLoad et accepte des options de chaîne `CHECK_CONSTRAINTS` telles `TABLOCK`que et.<br /><br /> Remarque : certaines des options de cette propriété ne sont pas disponibles dans **l’Éditeur de destination Excel**, mais peuvent être définies avec **l’Éditeur avancé**.|  
|OpenRowset|String|Lorsque AccessMode est `OpenRowset`, nom de la table ou de la vue à laquelle la destination OLE DB accède.|  
|OpenRowsetVariable|String|Lorsque AccessMode est `OpenRowset from Variable`, nom de la variable qui contient le nom de la table ou de la vue à laquelle la destination OLE DB accède.|  
|SqlCommand|String|Lorsque AccessMode a `SQL Command`la valeur, l’instruction Transact-SQL que la destination OLE DB utilise pour spécifier les colonnes de destination pour les données.|  
  
 L'entrée et les colonnes d'entrée de la destination OLE DB ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [OLE DB Destination](ole-db-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
