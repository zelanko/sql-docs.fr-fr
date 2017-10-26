---
title: "Diagnostic de la gestion des règles | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7cfd05e9c41fee1e0a753e2c4e4fa4f86db641b3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostic-handling-rules"></a>Règles de gestion des Diagnostics
Les règles suivantes régissent la gestion de diagnostic dans **SQLGetDiagRec** et **SQLGetDiagField**.  
  
 Pour tous les composants ODBC :  
  
-   Doit pas remplacer, de modifier ou masquer les erreurs ou avertissements provenant d’un autre composant ODBC.  
  
-   Peut d’ajouter un enregistrement d’état supplémentaires lorsqu’ils reçoivent un message de diagnostic à partir d’un autre composant ODBC. L’enregistrement ajouté doit ajouter la valeur des informations réelles dans le message d’origine.  
  
 Pour ODBC composant interfaces directement une source de données :  
  
-   Devez faire précéder son identificateur de fournisseur, son identificateur de composant et identificateur de la source de données pour le message de diagnostic qu’il reçoit à partir de la source de données.  
  
-   Code d’erreur native de la source de données doit conserver les.  
  
-   Doit conserver les messages de diagnostic de la source de données.  
  
 Pour n’importe quel composant ODBC qui génère une erreur ou un avertissement, indépendamment de la source de données :  
  
-   Doit fournir le SQLSTATE approprié pour l’erreur ou l’avertissement.  
  
-   Doit générer le texte du message de diagnostic.  
  
-   Devez faire précéder son identificateur de fournisseur et de son identificateur de composant pour le message de diagnostic.  
  
-   Doit de retourner un code d’erreur natif, si un est disponible et explicite.  
  
 Pour le composant ODBC qui sert d’interface avec le Gestionnaire de pilotes :  
  
-   Les arguments de sortie doit s’initialiser **SQLGetDiagRec** et **SQLGetDiagField**.  
  
-   Doit mettre en forme et retourner les informations de diagnostic en tant qu’arguments de sortie de **SQLGetDiagRec** et **SQLGetDiagField** lorsque cette fonction est appelée.  
  
 Pour un composant ODBC autre que le Gestionnaire de pilotes :  
  
-   Doit définir la valeur SQLSTATE en fonction de l’erreur. Pour les pilotes basés sur des fichiers et pilotes basés sur SGBD qui n’utilisent pas une passerelle, le pilote doit définir la valeur SQLSTATE. Pour les pilotes basés sur SGBD qui utilisent une passerelle, le pilote ou une passerelle qui prend en charge ODBC peut-être définir la valeur SQLSTATE.

