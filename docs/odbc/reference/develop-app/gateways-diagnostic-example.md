---
title: Exemple de Diagnostic de passerelles | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f4e17074616111ee93ce87c04036d1fc3fd48dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062417"
---
# <a name="gateways-diagnostic-example"></a>Exemple de diagnostic des passerelles
Dans une architecture de la passerelle, un pilote envoie des demandes à une passerelle qui prend en charge ODBC. La passerelle envoie les demandes à un SGBD. Étant donné que c’est le composant qui sert d’interface avec le Gestionnaire de pilotes, le pilote met en forme et retourne les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si une passerelle à Rdb basé sur Oracle sur Microsoft Open Data Services et si Rdb n’a pas trouvé la table EMPLOYEE, la passerelle peut générer ce message de diagnostic :  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, la passerelle ajoutée un préfixe de l’identificateur de source de données ([Rdb]) pour le message de diagnostic. Étant donné que la passerelle a été le composant connectée à la source de données, il ajouté préfixes pour son fournisseur [DEC (]) et l’identificateur ([ODS passerelle]) pour le message de diagnostic. Il également ajouté la valeur SQLSTATE et le code d’erreur Rdb au début du message de diagnostic. Cela autorisé pour préserver la sémantique de sa propre structure de message et de toujours fournir les informations de diagnostic pour le pilote ODBC. Le pilote analyse les informations d’erreur associées à l’instruction d’erreur par la passerelle.  
  
 Étant donné que le pilote de la passerelle est le composant qui sert d’interface avec le Gestionnaire de pilotes, il utilise le message de diagnostic précédent pour formater et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
