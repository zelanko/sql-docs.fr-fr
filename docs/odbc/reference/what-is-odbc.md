---
title: Qu’est-ce que ODBC ? | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951798"
---
# <a name="what-is-odbc"></a>Qu’est-ce que ODBC ?
Il existe plusieurs idées fausses à propos d’ODBC dans le monde informatique. Il est à l’utilisateur final, une icône dans le panneau de configuration Microsoft® Windows®. Pour les programmeurs d’applications, il est une bibliothèque contenant les routines d’accès aux données. Beaucoup d’autres, il est la réponse à tous les problèmes d’accès de base de données imaginé.  
  
 Tout d’abord, ODBC est une spécification pour une API de base de données. Cette API est indépendante de tout un SGBD ou le système d’exploitation ; Bien que ce manuel utilise C, l’API ODBC est indépendant du langage. L’API ODBC est basé sur les spécifications de l’interface CLI à partir d’Open Group et ISO/IEC. ODBC 3. *x* entièrement implémente à la fois de ces spécifications - versions antérieures d’ODBC étaient basés sur des versions préliminaires de ces spécifications, mais n’implémentent pas entièrement les - et ajoute des fonctionnalités couramment requises par les développeurs de basée sur l’écran applications de base de données, telles que des curseurs avec défilement.  
  
 Les fonctions de l’API ODBC sont implémentées par les développeurs de pilotes spécifiques au SGBD. Applications appellent les fonctions de ces pilotes pour accéder aux données d’une manière indépendante du SGBD. Un gestionnaire de pilotes gère la communication entre les applications et pilotes.  
  
 Bien que Microsoft fournit un gestionnaire de pilotes pour les ordinateurs exécutant Microsoft Windows® 95 et versions ultérieures, a écrit plusieurs pilotes ODBC et appelle les fonctions ODBC à partir de certaines de ses applications, tout le monde peut écrire des pilotes et les applications ODBC. En fait, la grande majorité des applications ODBC et les pilotes disponibles aujourd'hui sont écrits par des entreprises autres que Microsoft. En outre, les applications et pilotes ODBC existent sur le Macintosh® et une variété de plates-formes UNIX.  
  
 Pour aider les développeurs d’applications et des pilotes, Microsoft propose un Kit de développement de logiciel (SDK) ODBC pour les ordinateurs exécutant Windows 95 et versions ultérieures qui fournit le Gestionnaire de pilotes, les DLL d’installation, les outils de test et les exemples d’applications. Microsoft s’est associé avec le logiciel Visigenic porter ces kits de développement logiciel pour les ordinateurs Macintosh et une variété de plates-formes UNIX.  
  
 Il est important de comprendre que ODBC est conçu pour exposer les fonctionnalités de base de données, pas les compléter. Par conséquent, les rédacteurs d’application ne doivent pas attendre que l’utilisation d’ODBC soudainement transforme une simple base de données en un moteur de base de données relationnelle complet. Ni sont les rédacteurs de pilotes attendus pour implémenter des fonctionnalités non disponibles dans la base de données sous-jacente. Une exception à cela est que les développeurs qui écrivent des pilotes qui accèdent directement aux données de fichier (par exemple, les données dans un fichier Xbase) sont requis pour écrire un moteur de base de données qui prend en charge des fonctionnalités SQL au moins minimales. Une autre exception qui est le composant ODBC du SDK Windows, précédemment inclus dans le Kit de développement logiciel Microsoft Data Access Components (MDAC), fournit une bibliothèque de curseurs qui simule des curseurs avec défilement pour les pilotes qui implémentent un certain niveau de fonctionnalité.  
  
 Les applications qui utilisent ODBC sont tenues de toutes les fonctionnalités entre bases de données. Par exemple, ODBC n’est pas un moteur de jointure hétérogène, ni est-il un processeur de transaction distribuée. Toutefois, car il est indépendant du SGBD, il peut servir à générer ces outils de bases de données croisées.
