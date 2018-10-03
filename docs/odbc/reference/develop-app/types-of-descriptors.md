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
manager: craigg
ms.openlocfilehash: a042229e3149f97b72b6e86b485771966eb80c30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797287"
---
# <a name="types-of-descriptors"></a>Types de descripteurs
Un descripteur est utilisé pour décrire l’un des éléments suivants :  
  
-   Un ensemble de zéro ou plusieurs paramètres. Un descripteur de paramètre peut être utilisé pour décrire :  
  
    -   Le *tampon de paramètre d’application,* qui contient les arguments dynamiques d’entrée en tant que jeu par l’application ou les arguments dynamique de sortie après l’exécution d’un **appeler** instruction SQL.  
  
    -   Le *mémoire tampon de paramètre de mise en œuvre*. Pour les arguments d’entrée dynamiques, il contient les mêmes arguments que le tampon de paramètre d’application, après toute conversion de données que l’application peut spécifier. Pour les arguments de sortie dynamique, il contient les arguments retournés, avant toute conversion de données que l’application peut spécifier.  
  
     Pour les arguments d’entrée dynamiques, l’application doit fonctionner sur un descripteur de paramètre d’application avant d’exécuter une instruction SQL qui contient des marqueurs de paramètres dynamiques. Pour les arguments d’entrée et de sortie de dynamiques, l’application peut spécifier différents types de données de celles figurant dans le descripteur de paramètre de mise en œuvre pour atteindre la conversion de données.  
  
-   Une seule ligne de base de données. Un descripteur de ligne peut être utilisé pour décrire :  
  
    -   Le *tampon de ligne d’implémentation,* qui contient la ligne à partir de la base de données. (Ces mémoires tampons sur le plan conceptuel contiennent des données écrites dans ou lire à partir de la base de données. Toutefois, le formulaire stocké de base de données n’est pas spécifié. Une base de données peut effectuer de conversion supplémentaire sur les données à partir de sa forme dans la mémoire tampon d’implémentation.)  
  
    -   Le *tampon de ligne d’application,* qui contient la ligne de données, tel que présenté à l’application, en suivant toute conversion de données que l’application peut spécifier.  
  
     L’application fonctionne sur le descripteur de ligne d’application dans tous les cas où les données de la colonne à partir de la base de données doivent apparaître dans les variables d’application. Pour obtenir la conversion des données de colonne de données, l’application peut spécifier différents types de données de celles figurant dans le descripteur de ligne d’implémentation.  
  
 Les types de descripteur sont résumées dans le tableau suivant.  
  
|Type de tampon|Lignes|Paramètres dynamiques|  
|-----------------|----------|------------------------|  
|**Mémoire tampon d’application**|descripteur de ligne d’application (ARD)|descripteur de paramètre d’application (APD)|  
|**Mémoire tampon d’implémentation**|descripteur de ligne d’implémentation (IRD)|descripteur de paramètre d’implémentation (IPD)|  
  
 Pour le paramètre ou les mémoires tampons de ligne, si l’application spécifie les différents types de données dans les enregistrements correspondants des descripteurs de mise en œuvre et d’application, le pilote effectue conversion de données lorsqu’il utilise les descripteurs. Par exemple, il peut convertir des valeurs numériques et datetime au format de chaîne de caractères. (Pour les conversions valides, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Un descripteur peut effectuer des rôles différents. Instructions différentes peuvent partager le descripteur de l’application alloue explicitement. Un descripteur de ligne dans une seule instruction peut servir d’un descripteur de paramètre dans une autre instruction.  
  
 Il est toujours connue si un descripteur donné est un descripteur d’application ou un descripteur d’implémentation, même si le descripteur n’a pas encore été utilisé dans une opération de base de données. Pour les descripteurs de l’implémentation alloue implicitement, l’implémentation enregistre la ligne prédéfinie par rapport au descripteur d’instruction. Descripteur qui alloue de l’application en appelant **SQLAllocHandle** est un descripteur d’application.
