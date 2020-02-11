---
title: Types de descripteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], types
ms.assetid: ec20e446-e540-41ad-8559-d9c0a5b8358f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d9d4a7572131afeeb0017d3773b72d899052b32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087791"
---
# <a name="types-of-descriptors"></a>Types de descripteurs
Un descripteur est utilisé pour décrire l’un des éléments suivants :  
  
-   Ensemble de zéro ou plusieurs paramètres. Un descripteur de paramètre peut être utilisé pour décrire les éléments suivants :  
  
    -   La *mémoire tampon de paramètres d’application,* qui contient soit les arguments dynamiques d’entrée définis par l’application, soit les arguments dynamiques de sortie après l’exécution d’une instruction **Call** de SQL.  
  
    -   *Mémoire tampon des paramètres d’implémentation*. Pour les arguments dynamiques d’entrée, cela contient les mêmes arguments que la mémoire tampon de paramètres d’application, après toute conversion de données que l’application peut spécifier. Pour les arguments dynamiques de sortie, contient les arguments retournés, avant toute conversion de données que l’application peut spécifier.  
  
     Pour les arguments dynamiques d’entrée, l’application doit fonctionner sur un descripteur de paramètre d’application avant d’exécuter une instruction SQL qui contient des marqueurs de paramètres dynamiques. Pour les arguments dynamiques d’entrée et de sortie, l’application peut spécifier des types de données différents de ceux du descripteur de paramètre d’implémentation pour permettre la conversion des données.  
  
-   Une seule ligne de données de base de données. Un descripteur de ligne peut être utilisé pour décrire les éléments suivants :  
  
    -   La *mise en mémoire tampon de ligne d’implémentation,* qui contient la ligne de la base de données. (Ces mémoires tampons contiennent conceptuellement des données écrites ou lues dans la base de données. Toutefois, le formulaire stocké des données de la base de données n’est pas spécifié. Une base de données peut effectuer une conversion supplémentaire sur les données à partir de son formulaire dans la mémoire tampon d’implémentation.)  
  
    -   La *mémoire tampon de ligne de l’application,* qui contient la ligne de données telle qu’elle est présentée à l’application, à la suite de la conversion de données que l’application peut spécifier.  
  
     L’application fonctionne sur le descripteur de ligne d’application dans tous les cas où les données de colonne de la base de données doivent apparaître dans les variables d’application. Pour permettre la conversion des données de colonne, l’application peut spécifier des types de données différents de ceux du descripteur de ligne d’implémentation.  
  
 Les types de descripteurs sont résumés dans le tableau suivant.  
  
|Type de mémoire tampon|Lignes|Paramètres dynamiques|  
|-----------------|----------|------------------------|  
|**Mémoire tampon d’application**|Descripteur de ligne d’application (ARD)|Descripteur de paramètre d’application (APD)|  
|**Mémoire tampon d’implémentation**|Descripteur de ligne d’implémentation (IRD)|Descripteur de paramètre d’implémentation (IPD)|  
  
 Pour le paramètre ou les mémoires tampons de ligne, si l’application spécifie des types de données différents dans les enregistrements correspondants des descripteurs d’implémentation et d’application, le pilote effectue la conversion des données lorsqu’il utilise les descripteurs. Par exemple, il peut convertir des valeurs numériques et DateTime en format de chaîne de caractères. (Pour les conversions valides, consultez l' [annexe D : types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Un descripteur peut exécuter différents rôles. Différentes instructions peuvent partager n’importe quel descripteur que l’application alloue explicitement. Un descripteur de ligne dans une instruction peut servir de descripteur de paramètre dans une autre instruction.  
  
 Il est toujours connu si un descripteur donné est un descripteur d’application ou un descripteur d’implémentation, même si le descripteur n’a pas encore été utilisé dans une opération de base de données. Pour les descripteurs que l’implémentation alloue implicitement, l’implémentation enregistre la ligne prédéfinie par rapport au descripteur d’instruction. Tout descripteur que l’application alloue en appelant **SQLAllocHandle** est un descripteur d’application.
