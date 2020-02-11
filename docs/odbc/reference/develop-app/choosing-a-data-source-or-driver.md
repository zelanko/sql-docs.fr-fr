---
title: Choix d’une source de données ou d’un pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], selecting driver
- connecting to data source [ODBC], selecting data source
- data sources [ODBC], selecting
- ODBC drivers [ODBC], selecting
ms.assetid: 10aaf570-01ab-4478-8339-bdde2a5e3dd1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9aac31af80ff5774d464f76f130d2d113002e60a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001399"
---
# <a name="choosing-a-data-source-or-driver"></a>Choix d’une source de données ou d’un pilote
La source de données ou le pilote utilisé par une application est parfois codé en dur dans l’application. Par exemple, une application personnalisée écrite par un département MIS pour transférer des données d’une source de données vers une autre doit contenir les noms de ces sources de données. l’application ne fonctionnera pas avec d’autres sources de données. Un autre exemple est une application verticale, telle que celle utilisée pour l’entrée de commande. Une telle application utilise toujours la même source de données, qui a un schéma prédéfini connu par l’application.  
  
 D’autres applications sélectionnent la source de données ou le pilote au moment de l’exécution. Il s’agit généralement d’applications génériques qui effectuent des requêtes ad hoc, comme une feuille de calcul qui utilise ODBC pour importer des données. De telles applications répertorient généralement les sources de données ou les pilotes disponibles et permettent aux utilisateurs de choisir ceux qu’ils souhaitent utiliser. Le fait qu’une application générique répertorie les sources de données, les pilotes, ou les deux, dépend fréquemment si l’application utilise des pilotes SGBD ou basés sur des fichiers.  
  
 Les pilotes basés sur des SGBD nécessitent généralement un ensemble complexe d’informations de connexion, telles que l’adresse réseau, le protocole réseau, le nom de la base de données, etc. L’objectif d’une source de données est de masquer toutes ces informations. Par conséquent, le paradigme de source de données se prête à une utilisation avec des pilotes basés sur SGBD. Une application peut afficher une liste de sources de données à l’utilisateur de deux manières. Il peut appeler **SQLDriverConnect** avec le mot clé **DSN** (nom de la source de données) et aucune valeur associée. le gestionnaire de pilotes affichera une liste de noms de sources de données. Si l’application souhaite contrôler l’apparence de la liste, elle appelle **SQLDataSources** pour récupérer une liste des sources de données disponibles et construit sa propre boîte de dialogue. Cette fonction est implémentée par le gestionnaire de pilotes et peut être appelée avant le chargement de tous les pilotes. L’application appelle ensuite une fonction de connexion et lui transmet le nom de la source de données choisie.  
  
 Si aucune source de données n’est spécifiée, la source de données par défaut indiquée par les informations système est utilisée. (Pour plus d’informations, consultez [sous-clé par défaut](../../../odbc/reference/install/default-subkey.md).) Si **SQLConnect** est appelé à l’aide d’un argument *ServerName* qui est introuvable, qu’il s’agit d’un pointeur null ou qu’il est défini sur « Default », le gestionnaire de pilotes se connecte à la source de données par défaut. La source de données par défaut est également utilisée si la chaîne de connexion utilisée dans un appel à **SQLDriverConnect** ou **SQLBrowseConnect** contient le mot clé **DSN** défini sur « Default » ou si la source de données spécifiée est introuvable. En outre, la source de données par défaut est utilisée si la chaîne de connexion utilisée dans un appel à **SQLDriverConnect** ne contient pas le mot clé **DSN** .  
  
 Avec les pilotes basés sur des fichiers, il est possible d’utiliser un paradigme de fichier. Pour les données stockées sur l’ordinateur local, les utilisateurs savent souvent que leurs données se trouvent dans un fichier particulier, par exemple Employee. dbf. Au lieu de sélectionner une source de données inconnue, il est plus facile pour ces utilisateurs de sélectionner le fichier qu’ils connaissent. Pour implémenter cela, l’application appelle d’abord **SQLDrivers**. Cette fonction est implémentée par le gestionnaire de pilotes et peut être appelée avant le chargement de tous les pilotes. **SQLDrivers** retourne la liste des pilotes disponibles. elle retourne également les valeurs des mots clés **FileUsage** et **FileExtns** . Le mot clé **FileUsage** explique si les pilotes basés sur des fichiers traitent les fichiers en tant que tables, comme xbase ou bases de données, comme le fait Microsoft® Access. Le mot clé **FileExtns** répertorie les extensions de nom de fichier que le pilote reconnaît, par exemple. dbf pour un pilote xbase. À l’aide de ces informations, l’application construit une boîte de dialogue par le biais de laquelle l’utilisateur choisit un fichier. En fonction de l’extension du fichier choisi, l’application se connecte au pilote en appelant **SQLDriverConnect** avec le mot clé **Driver** .  
  
 Il n’y a rien à faire pour empêcher une application d’utiliser une source de données avec un pilote basé sur des fichiers ou d’appeler **SQLDriverConnect** avec le mot clé **Driver** pour se connecter à un pilote basé sur un SGBD. Voici plusieurs utilisations courantes du mot clé **Driver** pour les pilotes basés sur SGBD :  
  
-   **Impossible de créer des sources de données.** Par exemple, une application personnalisée peut utiliser un pilote et une base de données particuliers. Si le nom du pilote et toutes les informations requises pour se connecter à la base de données sont codés en dur dans l’application, les utilisateurs n’ont pas besoin de créer une source de données sur leur ordinateur pour exécuter l’application. Tout ce qu’ils doivent faire est d’installer l’application et le pilote.  
  
     L’inconvénient de cette méthode est que l’application doit être recompilée et redistribuée si les informations de connexion changent. Si un nom de source de données est codé en dur dans l’application au lieu d’informations de connexion complètes, chaque utilisateur doit modifier uniquement les informations contenues dans la source de données.  
  
-   **Accès à un SGBD donné une seule fois.** Par exemple, une feuille de calcul qui récupère des données en appelant des fonctions ODBC peut contenir le mot clé **Driver** pour identifier un pilote particulier. Étant donné que le nom du pilote est significatif pour tous les utilisateurs qui ont ce pilote, la feuille de calcul peut être transmise à ces utilisateurs. Si la feuille de calcul contenait un nom de source de données, chaque utilisateur devra créer la même source de données pour utiliser la feuille de calcul.  
  
-   **Exploration du système pour toutes les bases de données accessibles à un pilote particulier.** Pour plus d’informations, consultez [connexion avec SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md), plus loin dans cette section.
