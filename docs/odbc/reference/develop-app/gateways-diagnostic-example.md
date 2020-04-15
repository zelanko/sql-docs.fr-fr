---
title: Exemple diagnostique de passerelles Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18fd78be7be2eb79316339cbdf3d315deb194fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305570"
---
# <a name="gateways-diagnostic-example"></a>Exemple de diagnostic des passerelles
Dans une architecture de passerelle, un conducteur envoie des demandes à une passerelle qui prend en charge ODBC. La passerelle envoie les demandes à un DBMS. Parce que c’est le composant qui s’interface avec le Driver Manager, le pilote formate et renvoie les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si Oracle a basé une passerelle vers Rdb sur Microsoft Open Data Services et si Rdb ne pouvait pas trouver la table EMPLOYEE, la passerelle pourrait générer ce message diagnostique:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, la passerelle a ajouté un préfixe pour l’identifiant source de données ([Rdb]) au message diagnostique. Étant donné que la passerelle était le composant qui s’interface avec la source de données, elle a ajouté des préfixes pour son fournisseur ([DEC]) et son identifiant ([ODS Gateway]) au message diagnostique. Il a également ajouté la valeur SQLSTATE et le code d’erreur Rdb au début du message diagnostique. Cela lui a permis de préserver la sémantique de sa propre structure de message et de fournir encore l’information diagnostique de l’ODBC au conducteur. Le conducteur analyse les informations d’erreur jointes à l’énoncé d’erreur par la passerelle.  
  
 Parce que le conducteur de passerelle est le composant qui s’interface avec le Driver Manager, il utiliserait le message diagnostique précédent pour formater et retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
