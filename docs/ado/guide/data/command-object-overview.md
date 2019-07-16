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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925858"
---
# <a name="command-object-overview"></a>Vue d’ensemble de l’objet Command
Avec un **commande** de l’objet, vous pouvez procédez comme suit :  
  
-   Définir le texte exécutable de la commande (par exemple, une instruction SQL ou une procédure stockée) à l’aide de la **CommandText** propriété.  
  
-   Définir des requêtes paramétrables ou les arguments de procédure stockée à l’aide de **paramètre** objets et le **paramètres** collection.  
  
-   Exécuter une commande et retourner un **Recordset** de l’objet, le cas échéant, à l’aide de la **Execute** (méthode).  
  
-   Spécifiez le type de commande à l’aide de la **CommandType** propriété avant l’exécution pour optimiser les performances.  
  
-   Spécifier des informations spécifiques sur le texte de commande à l’aide de la **dialecte** propriété de la **commande** objet.  
  
-   Vérifier si le fournisseur enregistre une version préparée (ou compilée) de la commande avant l’exécution à l’aide de la **Prepared** propriété.  
  
-   Définir le nombre de secondes d’attente d’un fournisseur d’une commande à exécuter à l’aide de la **CommandTimeout** propriété.  
  
-   Associer une connexion ouverte avec un **commande** objet en définissant son **ActiveConnection** propriété.  
  
-   Définir le **nom** propriété pour identifier le **commande** objet en tant que méthode sur associé **connexion** objet.  
  
-   Passer un **commande** de l’objet à la **Source** propriété d’un **Recordset** afin d’obtenir des données.  
  
-   Passer un **Stream** objet contenant une commande (par exemple, une commande XML) à un fournisseur qui prend en charge.
