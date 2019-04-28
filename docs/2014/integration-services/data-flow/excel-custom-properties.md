---
title: Propriétés personnalisées d’Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8d556a199b608659a9ceaaeb3b7036155886d6c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827232"
---
# <a name="excel-custom-properties"></a>Propriétés personnalisées d'Excel
  **Propriétés personnalisées des sources**  
  
 La source Excel comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source Excel. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Entier|Mode utilisé pour accéder à la base de données. Les valeurs possibles sont **Open Rowset**, **OPENROWSET à partir de la Variable**, `SQL Command`, et **commande SQL à partir de la Variable**. La valeur par défaut est **Open Rowset**.|  
|CommandTimeout|Entier|Nombre de secondes accordées comme délai d'exécution d'une commande.  Une valeur égale à 0 indique un délai illimité.<br /><br /> **Remarque** Cette propriété n’est pas disponible dans l’ **Éditeur de source Excel**, mais elle peut être définie à l’aide de l’ **Éditeur avancé**.|  
|OpenRowset|String|Nom de l'objet de base de données utilisé pour ouvrir un ensemble de lignes.|  
|OpenRowsetVariable|String|Variable qui contient le nom de l'objet de base de données utilisé pour ouvrir un ensemble de lignes.|  
|ParameterMapping|String|Mappage des paramètres de la commande SQL en variables.|  
|SqlCommand|String|Commande SQL à exécuter.|  
|SqlCommandVariable|String|Variable qui contient la commande SQL à exécuter.|  
  
 La sortie et les colonnes de sortie de la source Excel ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Source Excel](excel-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination Excel comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination Excel. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (énumération)|Valeur qui spécifie la manière dont la destination accède à sa base de données de destination.<br /><br /> Cette propriété peut prendre les valeurs suivantes :<br /><br /> `OpenRowset` (0)-vous fournir le nom de la table ou vue.<br /><br /> `OpenRowset from Variable` (1)-vous fournir le nom d’une variable qui contient le nom de la table ou vue.<br /><br /> `OpenRowset Using Fastload` (3)-vous fournir le nom de la table ou vue.<br /><br /> `OpenRowset Using Fastload from Variable` (4)-vous fournir le nom d’une variable qui contient le nom de la table ou vue.<br /><br /> `SQL Command` (2)-vous fournissez une instruction SQL.|  
|CommandTimeout|Entier|Nombre maximal de secondes pendant lesquelles la commande SQL peut être exécutée avant d'arriver à expiration. Une valeur égale à **0** indique une durée illimitée. La valeur par défaut de cette propriété est **0**.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de destination Excel**, mais peut être définie avec **l’Éditeur avancé**.|  
|FastLoadKeepIdentity|Booléen|Valeur spécifiant si les valeurs d'identité doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement lorsque vous utilisez l'une des options de chargement rapide. La valeur par défaut de cette propriété est **False**.|  
|FastLoadKeepNulls|Booléen|Valeur spécifiant si les valeurs NULL doivent être copiées lors du chargement des données. Cette propriété est disponible uniquement avec l'une des options de chargement rapide. La valeur par défaut de cette propriété est **False**.|  
|FastLoadMaxInsertCommitSize|Entier|Valeur qui spécifie la taille du lot que la destination Excel tente de valider au cours des opérations de chargement rapide. La valeur par défaut est **2147483647**. La valeur **0** indique une opération de validation simple après le traitement de toutes les lignes.|  
|FastLoadOptions|String|Collection d'options de chargement rapide. Les options de chargement rapide incluent le verrouillage des tables et la vérification des contraintes. Vous pouvez spécifier une de ces options, les deux ou ni l'une ni l'autre.<br /><br /> Remarque : certaines des options de cette propriété ne sont pas disponibles dans **l’Éditeur de destination Excel**, mais peuvent être définies avec **l’Éditeur avancé**.|  
|OpenRowset|String|Quand AccessMode est `OpenRowset`, le nom de la table ou vue qui accède à la destination Excel.|  
|OpenRowsetVariable|String|Quand AccessMode est `OpenRowset from Variable`, le nom de la variable qui contient le nom de la table ou vue qui accède à la destination Excel.|  
|SqlCommand|String|Quand AccessMode est `SQL Command`, l’instruction Transact-SQL que la destination Excel utilise pour spécifier les colonnes de destination pour les données.|  
  
 L'entrée et les colonnes d'entrée de la destination Excel ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination Excel](excel-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
