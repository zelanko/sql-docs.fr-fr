---
title: Préparation et l’exécution de commandes | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], preparing and executing commands
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6bf2120468a00de2150f6105f4d79ec5a2ed4278
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700457"
---
# <a name="preparing-and-executing-commands"></a>Préparation et l’exécution de commandes
Les commandes sont émises pour un fournisseur des instructions pour effectuer certaines opérations sur la source de données sous-jacente. Une instruction SQL, par exemple, est une commande au fournisseur de données Microsoft SQL. Dans ADO, les commandes sont généralement représentées par **commande** objets, bien que des commandes simples peuvent également être émis via **connexion** ou **Recordset** objets.  
  
 Vous pouvez utiliser la **commande** objet pour demander de n’importe quel type d’opération pris en charge à partir du fournisseur, en supposant que le puisse interpréter correctement la chaîne de commande. Une opération courante pour les fournisseurs de données consiste à interroger une base de données et retourner des enregistrements dans une **Recordset** objet, qui peut être considéré comme un conteneur pour stocker le résultat et un outil pour afficher le résultat. À l’instar de nombreux objets ADO, certains **commande** collections d’objets, des méthodes ou propriétés peuvent générer des erreurs lorsque référencés, selon les fonctionnalités du fournisseur.  
  
 Outre l’utilisation de **commande** objets, vous pouvez utiliser la **Execute** méthode sur le **connexion** objet ou le **Open** sur la (méthode) **Jeu d’enregistrements** objet à émettre une commande et qu’il soit exécuté. Toutefois, vous devez utiliser un **commande** si vous avez besoin de réutiliser une commande dans votre code, ou si vous devez transmettre des informations de paramétrage avec votre commande de l’objet. Ces scénarios sont présentés plus en détail plus loin dans cette section.  
  
> [!NOTE]
>  Certains **commande**s peut retourner un jeu de résultats sous forme de flux binaire ou en tant qu’un seul **enregistrement** plutôt que comme un **Recordset**, si cela est pris en charge par le fournisseur. En outre, certains **commande**s ne sont pas destinées à retourner un résultat défini (par exemple, une requête de mise à jour SQL). Cette section décrit le scénario le plus courant, toutefois : l’exécution de **commande**s qui retournent des résultats comme un **Recordset** objet. Pour plus d’informations sur le renvoi des résultats dans **enregistrement**s ou **Stream**s, consultez [enregistrements et flux](../../../ado/guide/data/records-and-streams.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Vue d’ensemble de l’objet Command](../../../ado/guide/data/command-object-overview.md)  
  
-   [Création et exécution d’une commande simple](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Paramètres de l’objet Command](../../../ado/guide/data/command-object-parameters.md)  
  
-   [Appel d’une procédure stockée avec une commande](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [Appel d’une procédure stockée en tant que méthode sur un objet de connexion](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [Commandes nommées](../../../ado/guide/data/named-commands.md)  
  
-   [Passage de paramètres à une commande nommée](../../../ado/guide/data/passing-parameters-to-a-named-command.md)
