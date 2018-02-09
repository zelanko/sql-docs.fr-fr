---
title: "Vue d’ensemble de l’objet de commande | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 175c3793a41c4502a0c558c63e4eec89b35cd02f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="command-object-overview"></a>Vue d’ensemble de l’objet de commande
Avec un **commande** de l’objet, vous pouvez procédez comme suit :  
  
-   Définir le texte exécutable de la commande (par exemple, une instruction SQL ou une procédure stockée) à l’aide de la **CommandText** propriété.  
  
-   Définir des requêtes paramétrées ou des arguments de procédure stockée à l’aide de **paramètre** objets et la **paramètres** collection.  
  
-   Exécuter une commande et retourner un **Recordset** de l’objet, le cas échéant, à l’aide de la **Execute** (méthode).  
  
-   Spécifiez le type de commande à l’aide de la **CommandType** propriété avant l’exécution pour optimiser les performances.  
  
-   Spécifier des informations spécifiques sur le texte de commande à l’aide de la **dialecte** propriété de la **commande** objet.  
  
-   Contrôle si le fournisseur enregistre une version préparée (ou compilée) de la commande avant l’exécution à l’aide de la **Prepared** propriété.  
  
-   Définir le nombre de secondes d’attente d’un fournisseur d’une commande à exécuter à l’aide de la **CommandTimeout** propriété.  
  
-   Associer une connexion ouverte avec un **commande** objet en définissant ses **ActiveConnection** propriété.  
  
-   Définir le **nom** propriété pour identifier le **commande** objet comme une méthode sur associé **connexion** objet.  
  
-   Passer un **commande** de l’objet à la **Source** propriété d’un **Recordset** afin d’obtenir des données.  
  
-   Passez un **flux** objet contenant une commande (par exemple, une commande XML) à un fournisseur qui prend en charge.
