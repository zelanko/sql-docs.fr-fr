---
description: Messages de diagnostic
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d788a8bb23b7b63ae65a6fcf8c119110b5e6557
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461511"
---
# <a name="diagnostic-messages"></a>Messages de diagnostic
Un message de diagnostic est retourné avec chaque SQLSTATE. La même valeur SQLSTATE est souvent renvoyée avec plusieurs messages différents. Par exemple, SQLSTATE 42000 (erreur de syntaxe ou violation d’accès) est retourné pour la plupart des erreurs dans la syntaxe SQL. Toutefois, chaque erreur de syntaxe est susceptible d’être décrite par un autre message.  
  
 Les exemples de messages de diagnostic sont répertoriés dans la colonne erreur du tableau des SQLSTATEs dans l’annexe A et dans chaque fonction. Bien que les pilotes puissent retourner ces messages, ils sont plus susceptibles de retourner le message qui leur est transmis par la source de données.  
  
 Les applications affichent généralement les messages de diagnostic à l’utilisateur, ainsi que le code d’erreur SQLSTATE et Native. Cela permet à l’utilisateur et au personnel du support technique de déterminer la cause des problèmes. Les informations de composants incorporées dans le message sont particulièrement utiles pour cela.  
  
 Les messages de diagnostic proviennent de sources de données et de composants dans une connexion ODBC, tels que des pilotes, des passerelles et du gestionnaire de pilotes. En règle générale, les sources de données ne prennent pas directement en charge ODBC. Par conséquent, si un composant d’une connexion ODBC reçoit un message d’une source de données, il doit identifier la source de données comme étant la source du message. Il doit également s’identifier en tant que composant qui a reçu le message.  
  
 Si la source d’une erreur ou d’un avertissement est un composant lui-même, le message de diagnostic doit expliquer cela. Par conséquent, le texte des messages a deux formats différents. Pour les erreurs et les avertissements qui ne se produisent pas dans une source de données, le message de diagnostic doit utiliser le format suivant :  
  
 **[** *Vendor-identifier* **] [** *ODBC-Component-identifier* **]** *texte fourni par le composant*  
  
 Pour les erreurs et les avertissements qui se produisent dans une source de données, le message de diagnostic doit utiliser le format suivant :  
  
 **[** *Vendor-identifier* **] [** *ODBC-Component-identifier* **] [** *Data-source-identifier* **]** *Data-Source-fourni-Text*  
  
 Le tableau suivant indique la signification de chaque élément.  
  
|Élément|Signification|  
|-------------|-------------|  
|*identificateur du fournisseur*|Identifie le fournisseur du composant dans lequel l’erreur ou l’avertissement s’est produit ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*ODBC-Component-identifier*|Identifie le composant dans lequel l’erreur ou l’avertissement s’est produit ou qui a reçu l’erreur ou l’avertissement directement à partir de la source de données.|  
|*identificateur de source de données*|Identifie la source de données. Pour les pilotes basés sur des fichiers, il s’agit généralement d’un format de fichier, tel que xbase [1] pour les pilotes basés sur SGBD, il s’agit du produit SGBD.|  
|*texte fourni par le composant*|Généré par le composant ODBC.|  
|*Data-Source-fourni-texte*|Générée par la source de données.|  
  
 [1] dans ce cas, le pilote agit à la fois comme pilote et comme source de données.  
  
 Les crochets (**[]**) doivent être inclus dans le message et n’indiquent pas d’éléments facultatifs.
