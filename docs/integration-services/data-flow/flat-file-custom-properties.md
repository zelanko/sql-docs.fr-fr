---
title: Propriétés personnalisées des fichiers plats | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 00387fee6a11d3a2416d8440fdb7ae35665c472b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71292512"
---
# <a name="flat-file-custom-properties"></a>Propriétés personnalisées des fichiers plats

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  **Propriétés personnalisées des sources**  
  
 La source de fichier plat comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|String|Nom d'une colonne de sortie qui contient le nom de fichier. Si le nom n'est pas spécifié, aucune colonne de sortie contenant le nom de fichier ne sera générée.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
|RetainNulls|Boolean|Valeur qui spécifie si les valeurs NULL du fichier source doivent être conservées comme valeurs NULL lorsque les données sont traitées par le moteur du pipeline de transformation des données. La valeur par défaut de cette propriété est **False**.|  
  
 La sortie de la source de fichier plat n'est pas dotée de propriétés personnalisées.  
  
 Le tableau suivant décrit les propriétés personnalisées des colonnes de sortie de la source de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Valeur qui indique si la colonne utilise les routines d'analyse fournies par DTS (routines plus rapides mais qui ne tiennent pas compte des paramètres régionaux) ou les routines d'analyse standard qui tiennent compte des paramètres régionaux. Pour plus d'informations, consultez [Fast Parse](https://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95) et [Standard Parse](https://msdn.microsoft.com/library/dfe835b1-ea52-4e18-a23a-5188c5b6f013). La valeur par défaut de cette propriété est **False**.<br /><br /> Remarque : cette propriété n’est pas disponible dans **l’Éditeur de source de fichier plat**, mais elle peut être définie à l’aide de **l’éditeur avancé**.|  
  
 Pour plus d'informations, consultez [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
 **Propriétés personnalisées des destinations**  
  
 La destination de fichier plat comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de fichier plat. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|En-tête|String|Bloc de texte inséré dans le fichier avant l'écriture des données.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|Remplacer|Boolean|Valeur qui spécifie s'il faut remplacer un fichier de destination existant qui porte le même nom ou lui ajouter des données. La valeur par défaut de cette propriété est **True**.|  
  
 L'entrée et les colonnes d'entrée de la destination de fichier plat ne disposent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [Flat File Destination](../../integration-services/data-flow/flat-file-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
