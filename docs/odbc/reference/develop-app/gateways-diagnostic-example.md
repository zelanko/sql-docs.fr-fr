---
title: Exemple de diagnostic de passerelles | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305570"
---
# <a name="gateways-diagnostic-example"></a>Exemple de diagnostic des passerelles
Dans une architecture de passerelle, un pilote envoie des demandes à une passerelle qui prend en charge ODBC. La passerelle envoie les demandes à un SGBD. Étant donné qu’il s’agit du composant qui interagit avec le gestionnaire de pilotes, le pilote met en forme et retourne les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si Oracle est basé sur une passerelle RDB sur Microsoft Open Data Services et si RDB n’a pas pu trouver la table EMPLOYee, la passerelle peut générer ce message de diagnostic :  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, la passerelle a ajouté un préfixe pour l’identificateur de source de données ([RDB]) au message de diagnostic. Étant donné que la passerelle était le composant qui a été associé à la source de données, elle a ajouté des préfixes pour son fournisseur ([DEC]) et son identificateur ([ODS Gateway]) au message de diagnostic. Elle a également ajouté la valeur SQLSTATE et le code d’erreur RDB au début du message de diagnostic. Cela lui permettait de conserver la sémantique de sa propre structure de message tout en fournissant les informations de diagnostic ODBC au pilote. Le pilote analyse les informations d’erreur jointes à l’instruction Error par la passerelle.  
  
 Étant donné que le pilote de passerelle est le composant qui interagit avec le gestionnaire de pilotes, il utilise le message de diagnostic précédent pour formater et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
