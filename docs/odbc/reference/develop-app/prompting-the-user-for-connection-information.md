---
title: Invite l’utilisateur à fournir des informations de connexion | Microsoft Docs
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
ms.openlocfilehash: 7dfc63aaa6f162d382d6d8b3c627ff078c76825c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079066"
---
# <a name="prompting-the-user-for-connection-information"></a>Demande des informations de connexion à l’utilisateur
Si l’application utilise **SQLConnect** et doit inviter l’utilisateur à fournir des informations de connexion, telles qu’un nom d’utilisateur et un mot de passe, elle doit le faire lui-même. Bien que cela permette à l’application de contrôler son apparence, elle peut forcer l’application à contenir du code propre au pilote. Cela se produit lorsque l’application doit inviter l’utilisateur à fournir des informations de connexion spécifiques au pilote. Cela présente une situation impossible pour les applications génériques, qui sont conçues pour fonctionner avec tous les pilotes, y compris les pilotes qui n’existent pas lors de l’écriture de l’application.  
  
 **SQLDriverConnect** peut inviter l’utilisateur à fournir des informations de connexion. Par exemple, le programme personnalisé mentionné précédemment peut transmettre la chaîne de connexion suivante à **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Le pilote peut ensuite afficher une boîte de dialogue qui vous invite à entrer des ID utilisateur et des mots de passe, comme dans l’illustration suivante.  
  
 ![Boîte de dialogue qui demande l'ID d'utilisateur et le mot de passe](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Le pilote peut demander des informations de connexion est particulièrement utile pour les applications génériques et verticales. Ces applications ne doivent pas contenir d’informations spécifiques au pilote et le fait de demander au pilote les informations dont elle a besoin permet de conserver les informations de l’application. Cela est illustré par les deux exemples précédents. Lorsque l’application a passé uniquement le nom de la source de données au pilote, l’application ne contenait pas d’informations spécifiques au pilote et n’était donc pas liée à un pilote particulier. Lorsque l’application a passé une chaîne de connexion complète au pilote, elle est liée au pilote qui pourrait interpréter cette chaîne.  
  
 Une application générique peut prendre cette étape plus loin et ne pas même spécifier une source de données. Lorsque **SQLDriverConnect** reçoit une chaîne de connexion vide, le gestionnaire de pilotes affiche la boîte de dialogue suivante.  
  
 ![Boîte de dialogue Sélectionner une source de données](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Une fois que l’utilisateur a sélectionné une source de données, le gestionnaire de pilotes construit une chaîne de connexion qui spécifie cette source de données et la transmet au pilote. Le pilote peut ensuite inviter l’utilisateur à fournir les informations supplémentaires dont il a besoin.  
  
 Les conditions dans lesquelles le pilote invite l’utilisateur sont contrôlées par l’indicateur *DriverCompletion* ; Il existe des options pour toujours demander, demander si nécessaire ou ne jamais demander. Pour obtenir une description complète de cet indicateur, consultez la description de la fonction [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) .
