---
title: Workload, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e81ea0aac9cfe7676abba18bc7dffb2e1561597b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759792"
---
# <a name="workload-element-dta"></a>Workload, élément (Assistant Paramétrage de base de données)
  Spécifie la charge de travail à utiliser pour une session de paramétrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois pour chaque `DTAInput` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Démarrer et utiliser l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**Éléments enfants**|[Élément File &#40;Assistant Paramétrage de base de données&#41;](file-element-dta.md)<br /><br /> [Élément Database &#40;Assistant Paramétrage de base de données&#41;](database-element-for-workload-dta.md)<br /><br /> [Élément EventString &#40;Assistant Paramétrage de base de données&#41;](eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Une charge de travail est un ensemble d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui s'exécute sur une ou plusieurs bases de données que vous souhaitez paramétrer. L'Assistant Paramétrage du moteur de base de données peut utiliser des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , des fichiers de trace et des tables de trace en tant que charges de travail.  
  
 Si vous spécifiez une charge de travail dans un fichier d'entrée XML et une charge de travail dans une ligne de commande avec l'outil **dta** , la charge de travail spécifiée dans la ligne de commande est utilisée pour le paramétrage. Toutes les options de paramétrage de la ligne de commande remplacent celles spécifiées dans un fichier d'entrée XML. Une seule exception : configuration spécifiée par l'utilisateur entrée dans le mode évaluation dans le fichier d'entrée XML. Par exemple, si une configuration est entrée dans l'élément `Configuration` du fichier d'entrée XML et que l'élément `EvaluateConfiguration` est également configuré en tant qu'une des options de paramétrage, les options de paramétrage spécifiées dans le fichier d'entrée remplacent toute option de paramétrage saisie dans la ligne de commande.  
  
 Une charge de travail doit être spécifiée pour chaque session de paramétrage.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie la **MyDatabase.MyDBOwner.TuningTable001** table de trace pour la `Workload` élément. La table **TuningTable001** a été créée à l'aide du modèle de paramétrage (Tuning) utilisé dans le Générateur de profils SQL Server et dont le résultat de trace a été enregistré comme table.  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
