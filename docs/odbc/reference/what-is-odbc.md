---
title: Qu’est-ce que ODBC ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: badf3a45-f941-44ae-a31d-393116f68a18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bda4abf9802bd58e81f35bd4223b28f687e89b4f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67951798"
---
# <a name="what-is-odbc"></a>Qu’est-ce que ODBC ?
De nombreuses inconceptions concernant ODBC existent dans le monde informatique. Pour l’utilisateur final, il s’agit d’une icône dans le panneau de configuration de Microsoft® Windows®. Pour le programmeur de l’application, il s’agit d’une bibliothèque contenant des routines d’accès aux données. Pour beaucoup d’autres choses, il s’agit de la réponse à tous les problèmes d’accès aux bases de données jamais imaginés.  
  
 Tout d’abord, ODBC est une spécification pour une API de base de données. Cette API est indépendante de tout SGBD ou système d’exploitation. Bien que ce manuel utilise C, l’API ODBC est indépendante du langage. L’API ODBC est basée sur les spécifications CLI de Open Group et ISO/IEC. ODBC 3. *x* implémente entièrement ces deux spécifications. les versions antérieures d’ODBC étaient basées sur des versions préliminaires de ces spécifications, mais ne les implémentaient pas entièrement, et ajoutent des fonctionnalités généralement requises par les développeurs d’applications de base de données à base d’écran, telles que les curseurs à défilement.  
  
 Les fonctions de l’API ODBC sont implémentées par les développeurs de pilotes spécifiques au SGBD. Les applications appellent les fonctions de ces pilotes pour accéder aux données d’une manière indépendante du SGBD. Un gestionnaire de pilotes gère la communication entre les applications et les pilotes.  
  
 Bien que Microsoft fournisse un gestionnaire de pilotes pour les ordinateurs exécutant Microsoft Windows® 95 et versions ultérieures, a écrit plusieurs pilotes ODBC et appelle des fonctions ODBC à partir de certaines de ses applications, tout le monde peut écrire des applications et des pilotes ODBC. En fait, la grande majorité des pilotes et des applications ODBC disponibles aujourd’hui sont écrites par des entreprises autres que Microsoft. En outre, les applications et pilotes ODBC existent sur le® Macintosh et sur diverses plateformes UNIX.  
  
 Pour aider les développeurs d’applications et de pilotes, Microsoft propose un kit de développement logiciel (SDK) ODBC pour les ordinateurs exécutant Windows 95 et versions ultérieures, qui fournit le gestionnaire de pilotes, la DLL d’installation, les outils de test et les exemples d’applications. Microsoft a associé au logiciel Visigenic pour porter ces kits de développement logiciel (SDK) sur le Macintosh et sur diverses plateformes UNIX.  
  
 Il est important de comprendre qu’ODBC est conçu pour exposer les fonctionnalités de base de données, et non les compléter. Ainsi, les créateurs d’applications ne doivent pas s’attendre à ce que l’utilisation d’ODBC transforme soudainement une base de données simple en un moteur de base de données relationnelle complet. Les writers de pilotes ne sont pas supposés implémenter les fonctionnalités introuvables dans la base de données sous-jacente. À titre d’exception, les développeurs qui écrivent des pilotes qui accèdent directement aux données d’un fichier (par exemple, les données d’un fichier xbase) sont tenus d’écrire un moteur de base de données qui prend en charge au moins une fonctionnalité SQL minimale. Une autre exception est que le composant ODBC de la SDK Windows, anciennement inclus dans le kit de développement logiciel (SDK) Microsoft Data Access Components (MDAC), fournit une bibliothèque de curseurs qui simule les curseurs défilants pour les pilotes qui implémentent un certain niveau de fonctionnalité.  
  
 Les applications qui utilisent ODBC sont responsables des fonctionnalités des bases de données croisées. Par exemple, ODBC n’est pas un moteur de jointure hétérogène, ni un processeur de transactions distribuées. Toutefois, étant donné qu’il est indépendant du SGBD, il peut être utilisé pour créer des outils de base de données croisée.
