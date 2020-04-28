---
title: Vue d’ensemble de l’objet de commande | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef68a36f64fbaf72f18af9fba6f2e2781422574c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925858"
---
# <a name="command-object-overview"></a>Vue d’ensemble de l’objet Command
Avec un objet **Command** , vous pouvez effectuer les opérations suivantes :  
  
-   Définissez le texte exécutable de la commande (par exemple, une instruction SQL ou une procédure stockée) à l’aide de la propriété **CommandText** .  
  
-   Définir des requêtes paramétrables ou des arguments de procédure stockée à l’aide d’objets de **paramètre** et de la collection **Parameters** .  
  
-   Exécutez une commande et retournez un objet **Recordset** , le cas échéant, à l’aide de la méthode **Execute** .  
  
-   Spécifiez le type de commande à l’aide de la propriété **CommandType** avant l’exécution pour optimiser les performances.  
  
-   Spécifiez des informations spécifiques sur le texte de la commande à l’aide de la propriété **Dialect** de l’objet **Command** .  
  
-   Contrôler si le fournisseur enregistre une version préparée (ou compilée) de la commande avant l’exécution à l’aide de la propriété **Prepared** .  
  
-   Définit le nombre de secondes pendant lesquelles un fournisseur attendra qu’une commande s’exécute à l’aide de la propriété **CommandTimeout** .  
  
-   Associez une connexion ouverte à un objet de **commande** en définissant sa propriété **ActiveConnection** .  
  
-   Définissez la propriété **Name** pour identifier l’objet **Command** comme une méthode sur l’objet **Connection** associé.  
  
-   Transmettez un objet **Command** à la propriété **source** d’un **Recordset** afin d’obtenir des données.  
  
-   Passer un objet de **flux** contenant une commande (par exemple, une commande XML) à un fournisseur qui le prend en charge.
