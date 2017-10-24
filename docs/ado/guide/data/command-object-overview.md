---
title: "Vue d’ensemble de l’objet de commande | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61d296aaafd3e610a244aa4e0831b9bed5ff5855
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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

