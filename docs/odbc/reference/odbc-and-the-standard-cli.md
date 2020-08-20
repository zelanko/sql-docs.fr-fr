---
description: ODBC et l’interface CLI standard
title: ODBC et l’interface CLI standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], CLI
- CLI [ODBC]
- CLI [ODBC], about CLI
- call-level interface [ODBC]
- call-level interface [ODBC], about call-level interface
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 844ca219bf912421cf859e0fc459b78d755fe159
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487382"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC et l’interface CLI standard
ODBC s’aligne sur les spécifications et normes suivantes qui traitent de l’interface de niveau appel (CLI). (Les fonctionnalités ODBC sont un sur-ensemble de chacune de ces normes.)  
  
-   La spécification Open Group IAO « Gestion des données : interface de niveau appel SQL (CLI) »  
  
-   Interface de niveau d’appel ISO/IEC 9075-3:1995 (E) (SQL/CLI)  
  
 À la suite de cet alignement, les conditions suivantes sont vraies :  
  
-   Une application écrite dans les spécifications Open Group et ISO CLI fonctionne avec un pilote ODBC *3. x* ou un pilote conforme aux normes lorsqu’elle est compilée avec les fichiers d’en-tête ODBC *3. x* et est liée aux bibliothèques ODBC *3. x* , et lorsqu’elle accède au pilote par le biais du gestionnaire de pilotes ODBC *3. x* .  
  
-   Un pilote écrit dans les spécifications Open Group et ISO CLI fonctionne avec une application ODBC *3. x* ou une application conforme aux normes lorsqu’elle est compilée avec les fichiers d’en-tête ODBC *3. x* et est liée aux bibliothèques ODBC *3. x* , et lorsque l’application accède au pilote par le biais du gestionnaire de pilotes ODBC *3. x* . (Pour plus d’informations, consultez [applications et pilotes conformes aux normes](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Le niveau de conformité de l’interface principale englobe toutes les fonctionnalités de l’interface CLI ISO et toutes les fonctionnalités non facultatives de l’interface CLI Open Group. Les fonctionnalités facultatives de l’interface CLI Open Group s’affichent dans des niveaux de conformité d’interface plus élevés. Étant donné que tous les pilotes ODBC *3. x* sont requis pour prendre en charge les fonctionnalités dans le niveau de conformité de l’interface principale, les conditions suivantes sont vraies :  
  
-   Un pilote ODBC *3. x* prend en charge toutes les fonctionnalités utilisées par une application conforme aux normes.  
  
-   Une application ODBC *3. x* qui utilise uniquement les fonctionnalités de la CLI ISO et les fonctionnalités non facultatives de l’interface CLI Open Group fonctionne avec tous les pilotes conformes aux normes.  
  
 Outre les spécifications de l’interface au niveau de l’appel contenues dans les normes de l’interface de commande de groupe ISO/CEI et Open Group, ODBC implémente les fonctionnalités suivantes. (Certaines de ces fonctionnalités existaient dans les versions d’ODBC antérieures à ODBC *3. x*.)  
  
-   Extractions multiligne par un appel de fonction unique  
  
-   Liaison à un tableau de paramètres  
  
-   Prise en charge des signets incluant l’extraction par signet, les signets de longueur variable et les mises à jour en bloc et les suppressions par signet sur les lignes non contiguës  
  
-   Liaison selon les lignes  
  
-   Décalages de liaison  
  
-   Prise en charge des lots d’instructions SQL, qu’il s’agisse d’une procédure stockée ou d’une séquence d’instructions SQL exécutées à l’aide de **SQLExecute** ou **SQLExecDirect**  
  
-   Nombre exact ou approximatif de lignes de curseur  
  
-   Opérations de mise à jour et de suppression positionnées et mises à jour et suppressions par lot par appel de fonction (**SQLSetPos**)  
  
-   Fonctions de catalogue qui extraient des informations du schéma d’informations sans avoir besoin de prendre en charge les vues de schémas d’informations  
  
-   Séquences d’échappement pour les jointures externes, les fonctions scalaires, les littéraux datetime, les littéraux d’intervalle et les procédures stockées  
  
-   Bibliothèques de traduction de page de codes  
  
-   Rapport du niveau de conformité ANSI d’un pilote et de la prise en charge de SQL  
  
-   Remplissage automatique à la demande du descripteur de paramètre d’implémentation  
  
-   Tableaux d’état des diagnostics et des lignes et des paramètres améliorés  
  
-   Types de mémoire tampon d’application de type DateTime, Interval, Numeric/Decimal et 64 bits  
  
-   Exécution asynchrone  
  
-   Prise en charge des procédures stockées, y compris les séquences d’échappement, les mécanismes de liaison de paramètre de sortie et les fonctions de catalogue  
  
-   Améliorations de la connexion, notamment la prise en charge des attributs de connexion et de l’exploration des attributs
