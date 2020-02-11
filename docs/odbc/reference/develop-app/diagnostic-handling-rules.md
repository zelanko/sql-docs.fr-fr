---
title: Règles de gestion des diagnostics | Microsoft Docs
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
ms.openlocfilehash: 269e021d3fd4610c2fccda46bcd8ca160982543c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039918"
---
# <a name="diagnostic-handling-rules"></a>Règles de gestion des diagnostics
Les règles suivantes régissent la gestion des diagnostics dans **SQLGetDiagRec** et **SQLGetDiagField**.  
  
 Pour tous les composants ODBC :  
  
-   Ne doit pas remplacer, modifier ou masquer les erreurs ou les avertissements reçus d’un autre composant ODBC.  
  
-   Peut ajouter un enregistrement d’État supplémentaire lorsqu’ils reçoivent un message de diagnostic d’un autre composant ODBC. L’enregistrement ajouté doit ajouter la valeur des informations réelles au message d’origine.  
  
 Pour le composant ODBC qui interface directement une source de données :  
  
-   Doit préfixer son identificateur de fournisseur, son identificateur de composant et l’identificateur de la source de données au message de diagnostic qu’il reçoit de la source de données.  
  
-   Doit conserver le code d’erreur natif de la source de données.  
  
-   Doit conserver le message de diagnostic de la source de données.  
  
 Pour tout composant ODBC qui génère une erreur ou un avertissement indépendant de la source de données :  
  
-   Vous devez fournir le SQLSTATE correct pour l’erreur ou l’avertissement.  
  
-   Doit générer le texte du message de diagnostic.  
  
-   Doit préfixer son identificateur de fournisseur et son identificateur de composant au message de diagnostic.  
  
-   Doit retourner un code d’erreur natif, s’il est disponible et significatif.  
  
 Pour le composant ODBC qui s’interface avec le gestionnaire de pilotes :  
  
-   Doit initialiser les arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField**.  
  
-   Doit mettre en forme et retourner les informations de diagnostic en tant qu’arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField** lorsque cette fonction est appelée.  
  
 Pour un composant ODBC autre que le gestionnaire de pilotes :  
  
-   La valeur SQLSTATE doit être définie en fonction de l’erreur native. Pour les pilotes basés sur des fichiers et les pilotes SGBD qui n’utilisent pas de passerelle, le pilote doit définir la valeur SQLSTATE. Pour les pilotes basés sur SGBD qui utilisent une passerelle, le pilote ou une passerelle qui prend en charge ODBC peut définir SQLSTATE.
