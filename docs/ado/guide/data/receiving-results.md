---
title: "Réception des résultats | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5768404342f76eb8c5999678e6c1a4aa4a3bcd42
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="receiving-results"></a>Réception des résultats
La plupart des commandes ADO traduire certaines informations retournées à l’appelant. Pour retourner l’ensemble de lignes de commandes, les résultats sont reçus dans un **Recordset** objet, qui est probablement la plus utilisée des objets ADO.  
  
 Il existe plusieurs façons pour recevoir des données dans un **Recordset** objet à partir d’une source de données, y compris l’appel de ce qui suit :  
  
-   [Connection.Execute (méthode)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Méthode Command.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset.Open (méthode)](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Recevoir des données dans un **Recordset** objet conclut le processus d’obtention de données, avec la participation d’un **connexion** objet et un **commande** de l’objet, implicitement ou explicitement. Dans un système d’applications client/serveur classique, l’ensemble du processus d’obtention de données requiert un aller-retour sur le réseau pour chaque rempli **Recordset**.  
  
 Pour recevoir plusieurs jeux de résultats signifie que vous devez effectuer plusieurs allers-retours sur le réseau, une pour chaque jeu de données encapsulée dans un **Recordset** objet. Pour les réseaux lents ou encombrés, ce qui réduit le nombre d’allers-retours peut-être aider à améliorer les performances de l’application. Par conséquent, certains fournisseurs offrent la prise en charge pour la réception de plusieurs **Recordset**s dans un seul aller-retour. Cela est décrit dans la rubrique suivante :  
  
-   [Réception de plusieurs jeux d’enregistrements](../../../ado/guide/data/receiving-multiple-recordsets.md)

