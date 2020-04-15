---
title: Règles de manutention diagnostique (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f7f9d19a5a369e9da0efbc0d62f8e556b0597c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305840"
---
# <a name="diagnostic-handling-rules"></a>Règles de gestion des diagnostics
Les règles suivantes régissent la manipulation diagnostique dans **SQLGetDiagRec** et **SQLGetDiagField**.  
  
 Pour tous les composants ODBC :  
  
-   Ne doit pas remplacer, modifier ou masquer les erreurs ou avertissements reçus d’un autre composant ODBC.  
  
-   Peut ajouter un enregistrement d’état supplémentaire lorsqu’ils reçoivent un message diagnostique d’un autre composant ODBC. L’enregistrement supplémentaire doit ajouter une réelle valeur d’information au message original.  
  
 Pour le composant ODBC qui interface directement une source de données :  
  
-   Doit préfixer son identifiant fournisseur, son identifiant de composant et l’identifiant de la source de données au message diagnostique qu’il reçoit de la source de données.  
  
-   Doit préserver le code d’erreur natif de la source de données.  
  
-   Doit préserver le message diagnostique de la source de données.  
  
 Pour tout composant ODBC qui génère une erreur ou un avertissement indépendant de la source de données :  
  
-   Doit fournir le SQLSTATE correct pour l’erreur ou l’avertissement.  
  
-   Doit générer le texte du message diagnostique.  
  
-   Doit préfixer son identifiant fournisseur et son identifiant de composant au message diagnostique.  
  
-   Doit retourner un code d’erreur natif, si l’on est disponible et significatif.  
  
 Pour le composant ODBC qui s’interface avec le Driver Manager :  
  
-   Doit initialiser les arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField**.  
  
-   Doit formater et retourner l’information diagnostique comme arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField** lorsque cette fonction est appelée.  
  
 Pour un composant ODBC autre que le gestionnaire de conducteur :  
  
-   Doit définir le SQLSTATE en fonction de l’erreur native. Pour les conducteurs basés sur les fichiers et les conducteurs basés sur DBMS qui n’utilisent pas une passerelle, le conducteur doit définir le SQLSTATE. Pour les conducteurs basés sur DBMS qui utilisent une passerelle, soit le conducteur ou une passerelle qui prend en charge ODBC peut définir le SQLSTATE.
