---
title: ODBC et l’interface CLI Standard | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5485da176b9bd4aa7afca7afa088e6932d6f0d58
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814099"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC et l’interface CLI standard
ODBC s’aligne sur les spécifications et les normes qui traitent avec l’Interface de niveau d’appel (CLI) suivantes. (Les fonctions ODBC sont un sur-ensemble de chacun de ces normes.)  
  
-   La spécification d’IAO Open Group « gestion des données : Interface de niveau d’appel SQL (CLI) »  
  
-   ISO/IEC 9075-Interface de niveau d’appel 3:1995 (E) (SQL/CLI)  
  
 À la suite de cet alignement, les conditions suivantes sont réunies :  
  
-   Une application écrite aux Open Group et aux spécifications ISO CLI fonctionne avec un ODBC 3. *x* pilote ou un pilote conforme aux normes lorsqu’il est compilé avec l’ODBC 3. *x* en-tête des fichiers et lié avec ODBC 3. *x* bibliothèques, et quand il accède au pilote via l’ODBC 3. *x* Gestionnaire de pilotes.  
  
-   Un pilote écrit dans les spécifications Open Group et ISO CLI fonctionne avec un ODBC 3 *.x* application ou une application conforme aux normes lorsqu’il est compilé avec l’ODBC 3 *.x* en-tête des fichiers et lié avec ODBC 3 *.x* bibliothèques, et lorsque l’application accède au pilote via l’ODBC 3 *.x* Gestionnaire de pilotes. (Pour plus d’informations, consultez [Applications conformes aux normes et des pilotes](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md).  
  
 Niveau de la conformité de l’interface Core englobe toutes les fonctionnalités de la CLI ISO et toutes les fonctionnalités obligatoires dans l’interface CLI de groupe ouvert. Fonctionnalités facultatives de l’interface CLI de groupe ouvert s’affichent dans les niveaux de conformité interface supérieurs. Étant donné que tous les ODBC 3. *x* pilotes sont requis pour prendre en charge les fonctionnalités de niveau de la conformité de l’interface de Core, les conditions suivantes sont remplies :  
  
-   Une application ODBC 3. *x* pilote prendra en charge toutes les fonctionnalités utilisées par une application conforme aux normes.  
  
-   Une application ODBC 3. *x* application en utilisant uniquement les fonctionnalités de ISO CLI et les fonctionnalités obligatoires de l’interface CLI de groupe Ouvrir fonctionnera avec n’importe quel pilote conformes aux normes.  
  
 En plus des spécifications de l’interface de niveau d’appel contenues dans les normes ISO/CEI et l’interface CLI de groupe ouvert, ODBC implémente les fonctionnalités suivantes. (Certaines de ces fonctionnalités existaient dans les versions d’ODBC avant ODBC 3. *x*.)  
  
-   Extractions multilignes par un appel de fonction unique  
  
-   Liaison à un tableau de paramètres  
  
-   Prise en charge des signets, y compris l’extraction par signet, les signets de longueur variable et en bloc mettre à jour et supprimer des opérations de signet sur les lignes  
  
-   Liaison selon les lignes  
  
-   Décalages de liaison  
  
-   Prise en charge des lots d’instructions SQL, dans une procédure stockée ou comme une séquence d’instructions SQL exécutées via **SQLExecute** ou **SQLExecDirect**  
  
-   Le nombre de lignes du curseur exact ou approximatif  
  
-   Positionné de mise à jour et les opérations de suppression et les mises à jour par lot et les suppressions d’appel de fonction (**SQLSetPos**)  
  
-   Fonctions de catalogue qui extraient des informations à partir du schéma d’informations sans avoir besoin pour prendre en charge les vues de schémas d’informations  
  
-   Séquences d’échappement pour les jointures externes, les fonctions scalaires, les littéraux datetime, les littéraux d’intervalle et les procédures stockées  
  
-   Bibliothèques de traduction de page de codes  
  
-   Création de rapports de niveau de la conformité ANSI et la prise en charge SQL d’un pilote  
  
-   Remplissage automatique de la demande de descripteur de paramètre d’implémentation  
  
-   Diagnostics améliorés et des tableaux de statut de ligne et le paramètre  
  
-   Date/heure, intervalle, numérique/décimal et types de mémoires tampons d’application entier 64 bits  
  
-   Exécution asynchrone  
  
-   Prise en charge de la procédure stockée, y compris les séquences d’échappement, les mécanismes de liaison de paramètre de sortie et des fonctions de catalogue  
  
-   Améliorations de la connexion, y compris la prise en charge des attributs de connexion et de navigation de l’attribut
