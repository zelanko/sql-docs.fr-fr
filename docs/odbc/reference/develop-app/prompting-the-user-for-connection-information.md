---
title: Inviter l’utilisateur pour les informations de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58df84bf96306a2cfbc0567a3d5f6cb13514a06e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861894"
---
# <a name="prompting-the-user-for-connection-information"></a>Demande des informations de connexion à l’utilisateur
Si l’application utilise **SQLConnect** et besoins pour inviter l’utilisateur les informations de connexion, telles que le nom d’utilisateur et mot de passe, elle doit le faire lui-même. Bien que cela permet à l’application contrôler son « apparence », cela peut obliger l’application devant contenir le code spécifique au pilote. Cela se produit lorsque l’application doit inviter l’utilisateur pour les informations de connexion spécifiques au pilote. Cela présente une situation impossible pour les applications génériques, qui sont conçus pour fonctionner avec tous les pilotes, y compris les pilotes qui n’existent pas lorsque l’application est écrite.  
  
 **SQLDriverConnect** peut inviter l’utilisateur pour les informations de connexion. Par exemple, le programme personnalisé mentionné plus haut peut passer la chaîne de connexion à **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Le pilote peut ensuite afficher une boîte de dialogue vous invite à entrer pour l’ID utilisateur et mots de passe, similaires à l’illustration suivante.  
  
 ![Boîte de dialogue qui vous invite à entrer l’ID d’utilisateur et mots de passe](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Que le pilote peut demander des informations de connexion est particulièrement utile pour les applications génériques et verticales. Ces applications ne doivent pas contenir d’informations spécifiques au pilote, et avoir l’invite de pilote pour les informations que nécessaires conserve ces informations en dehors de l’application. Cela est illustré par les deux exemples précédents. Lorsque l’application a passé uniquement le nom de source de données pour le pilote, l’application ne contenait pas toutes les informations spécifiques au pilote et par conséquent pas liée à un pilote spécifique. Lorsque l’application a passé une chaîne de connexion complète pour le pilote, il a été lié au pilote qui peut interpréter cette chaîne.  
  
 Une application générique peut aller davantage et même pas spécifier une source de données. Lorsque **SQLDriverConnect** reçoit une chaîne de connexion vide, le Gestionnaire de pilotes affiche la boîte de dialogue suivante.  
  
 ![Boîte de dialogue Source de données Sélectionnez](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Une fois que l’utilisateur sélectionne une source de données, le Gestionnaire de pilotes construit une chaîne de connexion en spécifiant cette source de données et les transmet au pilote. Le pilote peut invitera l’utilisateur pour toutes les informations supplémentaires que requises.  
  
 Les conditions sous lesquelles le pilote invite l’utilisateur sont contrôlées par le *DriverCompletion* indicateur ; il existe des options demandent systématiquement, invite si nécessaire ou pour ne jamais demander. Pour obtenir une description complète de cet indicateur, consultez la [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.
