---
title: Messages diagnostiques (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be63e9d78960e40ac5e9ee016d2cfd868d99a922
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305830"
---
# <a name="diagnostic-messages"></a>Messages de diagnostic
Un message diagnostique est retourné avec chaque SQLSTATE. Le même SQLSTATE est souvent retourné avec un certain nombre de messages différents. Par exemple, SQLSTATE 42000 (erreur syntaxe ou violation d’accès) est retourné pour la plupart des erreurs dans la syntaxe SQL. Cependant, chaque erreur de syntaxe est susceptible d’être décrite par un message différent.  
  
 Les exemples de messages diagnostiques sont répertoriés dans la colonne d’erreur dans le tableau des SQLSTATEs à l’Annexe A et dans chaque fonction. Bien que les conducteurs puissent retourner ces messages, ils sont plus susceptibles de leur transmettre n’importe quel message transmis par la source de données.  
  
 Les applications affichent généralement des messages diagnostiques à l’utilisateur, ainsi que le SQLSTATE et le code d’erreur natif. Cela aide l’utilisateur et le personnel de soutien à déterminer la cause de tout problème. Les informations sur les composants intégrées dans le message sont particulièrement utiles pour ce faire.  
  
 Les messages diagnostiques proviennent de sources de données et de composants d’une connexion ODBC, tels que les conducteurs, les passerelles et le gestionnaire de conducteur. En règle générale, les sources de données ne prennent pas directement en charge ODBC. Par conséquent, si un composant d’une connexion ODBC reçoit un message d’une source de données, il doit identifier la source de données comme source du message. Il doit également s’identifier comme le composant qui a reçu le message.  
  
 Si la source d’une erreur ou d’un avertissement est un composant lui-même, le message diagnostique doit l’expliquer. Par conséquent, le texte des messages a deux formats différents. Pour les erreurs et les avertissements qui ne se produisent pas dans une source de données, le message diagnostique doit utiliser ce format :  
  
 **[** *[fournisseur-identifiant* **][** *ODBC-composant-identifiant* **]** *composant-fourni-texte*  
  
 Pour les erreurs et les avertissements qui se produisent dans une source de données, le message diagnostique doit utiliser ce format :  
  
 **[fournisseur-identifiant** *vendor-identifier* **][** *ODBC-composant-identifiant* **] [** *data-source-identifiant* **]** *data-source-supplied-text*  
  
 Le tableau suivant montre la signification de chaque élément.  
  
|Élément|Signification|  
|-------------|-------------|  
|*fournisseur-identifiant*|Identifie le fournisseur du composant dans lequel l’erreur ou l’avertissement s’est produit ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*ODBC-composant-identifiant*|Identifie le composant dans lequel l’erreur ou l’avertissement s’est produit ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*data-source-identificateur*|Identifie la source de données. Pour les pilotes basés sur des fichiers, il s’agit généralement d’un format de fichier, tel que Xbase[1] Pour les pilotes basés sur DBMS, c’est le produit DBMS.|  
|*texte fourni par les composants*|Généré par le composant ODBC.|  
|*data-source-fourni-texte*|Généré par la source de données.|  
  
 [1] Dans ce cas, le conducteur agit à la fois comme le conducteur et la source de données.  
  
 Les crochets **([ ]**) doivent être inclus dans le message et n’indiquent pas les éléments optionnels.
