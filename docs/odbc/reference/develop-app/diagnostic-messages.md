---
title: Messages de diagnostic | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic messages messages
- error messages [ODBC], diagnostic messages
- diagnostic messages [ODBC]
ms.assetid: 98027871-9901-476e-a722-ee58b7723c1f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 883cd29d8628f1e9270ae95a772c4d116b896710
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63034916"
---
# <a name="diagnostic-messages"></a>Messages de diagnostic
Un message de diagnostic est retourné avec chaque SQLSTATE. La même valeur SQLSTATE est souvent retournée avec un nombre de messages différents. Par exemple, SQLSTATE 42000 (syntaxe ou violation d’accès) est retournée pour la plupart des erreurs dans la syntaxe SQL. Toutefois, chaque erreur de syntaxe est susceptible d’être décrite par un autre message.  
  
 Exemples de messages de diagnostics sont répertoriées dans la colonne d’erreur dans la table de SQLSTATE dans l’annexe A, ainsi que dans chaque fonction. Bien que les pilotes peuvent retourner ces messages, ils sont plus susceptibles de renvoyer le message est transmis par la source de données.  
  
 Applications affichent généralement des messages de diagnostic à l’utilisateur, ainsi que les chaînes SQLSTATE et code d’erreur natif. Cela permet à l’utilisateur et le service de support technique déterminer la cause des problèmes. Informations sur les composant incorporées dans le message sont particulièrement utiles pour cette opération.  
  
 Messages de diagnostic proviennent de sources de données et des composants dans une connexion ODBC, telles que le Gestionnaire de pilotes, les passerelles et les pilotes. En règle générale, les sources de données ne gèrent pas directement ODBC. Par conséquent, si un composant dans une connexion ODBC reçoit un message à partir d’une source de données, elle doit identifier la source de données comme la source du message. Il doit également s’identifier en tant que le composant qui a reçu le message.  
  
 Si la source d’une erreur ou un avertissement est un composant lui-même, le message de diagnostic doive expliquer ceci. Par conséquent, le texte des messages a deux formats. Pour les erreurs et avertissements qui n’apparaissent pas dans une source de données, le message de diagnostic doit utiliser ce format :  
  
 **[** *vendor-identifier* **][** *ODBC-component-identifier* **]** *component-supplied-text*  
  
 Pour les erreurs et avertissements qui se produisent dans une source de données, le message de diagnostic doit utiliser ce format :  
  
 **[** *vendor-identifier* **][** *ODBC-component-identifier* **][** *data-source-identifier* **]** *data-source-supplied-text*  
  
 Le tableau suivant indique la signification de chaque élément.  
  
|Élément|Signification|  
|-------------|-------------|  
|*vendor-identifier*|Identifie le fournisseur du composant dans lequel l’erreur ou l’avertissement s’est produite ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*ODBC-component-identifier*|Identifie le composant dans lequel l’erreur ou l’avertissement s’est produite ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*data-source-identifier*|Identifie la source de données. Pour les pilotes basés sur fichier, il s’agit généralement d’un format de fichier, tels que les pilotes de SGBD pour Xbase [1], c’est le produit du SGBD.|  
|*component-supplied-text*|Généré par le composant ODBC.|  
|*data-source-supplied-text*|Généré par la source de données.|  
  
 [1] dans ce cas, le pilote se comporte comme le pilote et la source de données.  
  
 Crochets ( **[]** ) doit être inclus dans le message et n’indiquent pas les éléments facultatifs.
