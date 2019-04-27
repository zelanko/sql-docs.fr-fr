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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770989"
---
# <a name="ole-db-custom-properties"></a>Propriétés personnalisées OLE DB
  **Propriétés personnalisées des sources**  
  
 La source OLE DB comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source OLE DB. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Entier|Mode utilisé pour accéder à la base de données. Les valeurs possibles sont **Open Rowset**, **OPENROWSET à partir de la Variable**, `SQL Command`, et **commande SQL à partir de la Variable**. La valeur par défaut est **Open Rowset**.|  
|AlwaysUseDefaultCodePage|Booléen|Valeur qui indique s'il faut utiliser la valeur de la propriété `DefaultCodePage` pour chaque colonne ou tenter de dériver la page de codes à partir des paramètres régionaux de chaque colonne. La valeur par défaut de cette propriété est `False`.|  
|CommandTimeout|Entier|Nombre de secondes accordées comme délai d'exécution d'une commande. Une valeur égale à 0 indique un délai illimité.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source OLE DB**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|DefaultCodePage|Entier|Page de codes à utiliser lorsque les informations de page de codes ne sont pas disponibles depuis la source de données.|  
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
|AccessMode|Integer (énumération)|Valeur qui spécifie la manière dont la destination accède à sa base de données de destination.<br /><br /> Cette propriété peut prendre les valeurs suivantes :<br /><br /> `OpenRowset` (0): Vous indiquez le nom de la table ou vue.<br />`OpenRowset from Variable` (1): Vous indiquez le nom d’une variable qui contient le nom de la table ou vue.<br />`OpenRowset Using Fastload` (3): Vous indiquez le nom de la table ou vue.<br />`OpenRowset Using Fastload from Variable` (4): Vous indiquez le nom d’une variable qui contient le nom de la table ou vue.<br />`SQL Command` (2): Vous fournissez une instruction SQL.|  
|AlwaysUseDefaultCodePage|Booléen|Valeur qui indique s'il faut utiliser la valeur de la propriété `DefaultCodePage` pour chaque colonne ou tenter de dériver la page de codes à partir des paramètres régionaux de chaque colonne. La valeur par défaut de cette propriété est `False`.|  
|CommandTimeout|Entier|Nombre maximal de secondes pendant lesquelles la commande SQL peut être exécutée avant d'arriver à expiration. La valeur 0 indique un délai infini. La valeur par défaut de cette propriété est 0.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de destination OLE DB**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|DefaultCodePage|Entier|Page de codes par défaut associée à la destination OLE DB.|  
|FastLoadKeepIdentity|Booléen|Valeur spécifiant si les valeurs d'identité doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement avec l'une des options de chargement rapide. La valeur par défaut de cette propriété est `False`. Cette propriété correspond à la norme OLE DB [IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) propriété `SSPROP_FASTLOADKEEPIDENTITY`.|  
|FastLoadKeepNulls|Booléen|Valeur spécifiant si les valeurs NULL doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement avec l'une des options de chargement rapide. La valeur par défaut de cette propriété est `False`. Cette propriété correspond à la norme OLE DB [IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) propriété `SSPROP_FASTLOADKEEPNULLS`.|  
|FastLoadMaxInsertCommitSize|Entier|Valeur qui spécifie la taille du lot que la destination OLE DB tente de valider au cours des opérations de chargement rapide. La valeur par défaut ( **0**) indique une opération de validation simple après le traitement de toutes les lignes.|  
|FastLoadOptions|String|Collection d'options de chargement rapide. Les options de chargement rapide incluent le verrouillage des tables et la vérification des contraintes. Vous pouvez spécifier une de ces options, les deux ou ni l'une ni l'autre. Cette propriété correspond à la propriété OLE DB IRowsetFastLoad `SSPROP_FASTLOADOPTIONS` et accepte les options de chaîne telles que `CHECK_CONSTRAINTS` et `TABLOCK`.<br /><br /> Remarque : certaines des options de cette propriété ne sont pas disponibles dans **l’Éditeur de destination Excel**, mais peuvent être définies avec **l’Éditeur avancé**.|  
|OpenRowset|String|Quand AccessMode est `OpenRowset`, le nom de la table ou vue qui accède à la destination OLE DB.|  
|OpenRowsetVariable|String|Quand AccessMode est `OpenRowset from Variable`, le nom de la variable qui contient le nom de la table ou vue qui accède à la destination OLE DB.|  
|SqlCommand|String|Quand AccessMode est `SQL Command`, l’instruction Transact-SQL que la destination OLE DB utilise pour spécifier les colonnes de destination pour les données.|  
  
 L'entrée et les colonnes d'entrée de la destination OLE DB ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [OLE DB Destination](ole-db-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
