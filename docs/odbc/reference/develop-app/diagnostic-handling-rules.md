---
title: Diagnostic de gestion des règles | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f59953dee77453bb8b453a40a36d17e865a1fe5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792257"
---
# <a name="diagnostic-handling-rules"></a>Règles de gestion des diagnostics
Les règles suivantes régissent la gestion des diagnostics dans **SQLGetDiagRec** et **SQLGetDiagField**.  
  
 Pour tous les composants ODBC :  
  
-   Doit pas remplacer, modifier ou masquer les erreurs ou avertissements provenant d’un autre composant ODBC.  
  
-   Peut d’ajouter un enregistrement d’état supplémentaires lorsqu’ils reçoivent un message de diagnostic à partir d’un autre composant ODBC. L’enregistrement ajouté doit ajouter la valeur des informations réelles au message d’origine.  
  
 Pour ODBC composant interfaces directement une source de données :  
  
-   Devez faire précéder son identificateur de fournisseur, son identificateur de composant et identificateur de la source de données pour le message de diagnostic qu’il reçoit à partir de la source de données.  
  
-   Doit de conserver le code d’erreur native de la source de données.  
  
-   Doit conserver les messages de diagnostic de la source de données.  
  
 Pour n’importe quel composant ODBC qui génère une erreur ou un avertissement quelle que soit la source de données :  
  
-   Doit fournir le SQLSTATE approprié pour l’erreur ou l’avertissement.  
  
-   Doit générer le texte du message de diagnostic.  
  
-   Devez faire précéder son identificateur de fournisseur et de son identificateur de composant pour le message de diagnostic.  
  
-   Doit de retourner un code d’erreur natif, si une est disponible et explicite.  
  
 Pour le composant ODBC qui interagit avec le Gestionnaire de pilotes :  
  
-   Doit initialiser des arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField**.  
  
-   Doit mettre en forme et retourner les informations de diagnostic en tant qu’arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField** lorsque cette fonction est appelée.  
  
 Pour un composant ODBC autre que le Gestionnaire de pilotes :  
  
-   Doit définir la variable SQLSTATE basée sur l’erreur native. Pour les pilotes basés sur des fichiers et pilotes basés sur SGBD qui n’utilisent pas une passerelle, le pilote doit définir la variable SQLSTATE. Pour les pilotes basés sur SGBD qui utilisent une passerelle, le pilote ou une passerelle qui prend en charge ODBC peut-être définir la variable SQLSTATE.
