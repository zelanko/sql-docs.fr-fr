---
title: ODBC et le Standard CLI (fr) Microsoft Docs
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
ms.openlocfilehash: 56dc0ac73c77cbbb77943d2e9ba308796b259dbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305140"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC et l’interface CLI standard
ODBC s’aligne sur les spécifications et les normes suivantes qui traitent de l’interface de niveau d’appel (CLI). (Les caractéristiques oDBC sont un superset de chacune de ces normes.)  
  
-   Spécification CAE Open Group "Data Management: SQL Call-Level Interface (CLI)"  
  
-   ISO/IEC 9075-3:1995 (E) Interface de niveau d’appel (SQL/CLI)  
  
 À la suite de cet alignement, ce qui suit est vrai :  
  
-   Une application écrite aux spécifications Open Group et ISO CLI fonctionnera avec un pilote ODBC *3.x* ou un pilote conforme aux normes lorsqu’elle sera compilée avec les fichiers d’en-tête ODBC *3.x* et reliée aux bibliothèques ODBC *3.x,* et lorsqu’elle accède au pilote par l’intermédiaire du gestionnaire de conducteur ODBC *3.x.*  
  
-   Un pilote écrit selon les spécifications Open Group et ISO CLI travaillera avec une application ODBC *3.x* ou une application conforme aux normes lorsqu’il sera compilé avec les fichiers d’en-tête ODBC *3.x* et lié aux bibliothèques ODBC *3.x,* et lorsque l’application accède au pilote par l’intermédiaire du gestionnaire de conducteur ODBC *3.x.* (Pour plus d’informations, voir [Applications et pilotes conformes aux normes](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Le niveau de conformité à l’interface Core englobe toutes les fonctionnalités de l’ISO CLI et toutes les fonctionnalités nonoptionnelles de l’Open Group CLI. Les caractéristiques facultatives de l’Open Group CLI apparaissent dans des niveaux de conformation d’interface plus élevés. Étant donné que tous les pilotes ODBC *3.x* sont tenus de prendre en charge les fonctionnalités du niveau de conformité à l’interface Core, ce qui suit est vrai :  
  
-   Un pilote ODBC *3.x* prendra en charge toutes les fonctionnalités utilisées par une application conforme aux normes.  
  
-   Une application ODBC *3.x* utilisant uniquement les fonctionnalités dans ISO CLI et les caractéristiques nonoptionnelles de l’Open Group CLI fonctionnera avec n’importe quel pilote conforme aux normes.  
  
 En plus des spécifications d’interface au niveau des appels contenues dans les normes ISO/IEC et Open Group CLI, ODBC implémente les fonctionnalités suivantes. (Certaines de ces fonctionnalités existaient dans les versions d’ODBC avant ODBC *3.x*.)  
  
-   Multirow récupère par un seul appel de fonction  
  
-   Liaison à un éventail de paramètres  
  
-   Support de signet comprenant aller chercher par signet, signets variables, et mise à jour et suppression en vrac par des opérations de signets sur des rangées discontiguous  
  
-   Liaison selon les lignes  
  
-   Compensations contraignantes  
  
-   Prise en charge de lots de relevés SQL, soit dans le cadre d’une procédure stockée, soit sous forme de séquence de déclarations SQL exécutées par **SQLExecute** ou **SQLExecDirect**  
  
-   Nombre exact ou approximatif de rangée de curseurs  
  
-   Mise à jour et suppression des opérations positionnées et mises à jour et suppressions par appel de fonction (**SQLSetPos**)  
  
-   Catalogue des fonctions qui extraient des informations à partir du schéma d’information sans avoir besoin de points de vue sur les schémas d’information à l’appui  
  
-   Séquences d’évasion pour les jointures extérieures, fonctions scalaires, littérals de date, les littérals d’intervalle, et les procédures stockées  
  
-   Bibliothèques de traduction de pages de code  
  
-   Signalement du niveau ansI-conformance d’un conducteur et du support SQL  
  
-   Population automatique à la demande du descripteur de paramètres de mise en œuvre  
  
-   Amélioration des diagnostics et des tableaux d’état des lignes et des paramètres  
  
-   Date, intervalle, numérique/décimal, et 64 bits de type tampon d’application integer  
  
-   Exécution asynchrone  
  
-   Support de procédure stocké, y compris les séquences d’évacuation, les mécanismes de liaison des paramètres de sortie et les fonctions de catalogue  
  
-   Améliorations de connexion, y compris la prise en charge des attributs de connexion et la navigation d’attribut
