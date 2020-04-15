---
title: Choisir une source de données ou un pilote Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b10aafad95463f56ec0f5a029eac59a02cff003b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303370"
---
# <a name="choosing-a-data-source-or-driver"></a>Choix d’une source de données ou d’un pilote
La source de données ou le pilote utilisé par une application est parfois codé dur dans l’application. Par exemple, une application personnalisée rédigée par un service MIS pour transférer des données d’une source de données à une autre contiendrait les noms de ces sources de données - l’application ne fonctionnerait tout simplement pas avec d’autres sources de données. Un autre exemple est une application verticale, comme celle utilisée pour l’entrée de commande. Une telle application utilise toujours la même source de données, qui a un schéma prédéfini connu par l’application.  
  
 D’autres applications sélectionnent la source de données ou le pilote au moment de l’exécution. Habituellement, il s’agit d’applications génériques qui font des requêtes ad hoc, comme une feuille de calcul qui utilise ODBC pour importer des données. Ces applications répertorient généralement les sources de données ou les pilotes disponibles et permettent aux utilisateurs de choisir ceux avec qui ils veulent travailler. La question de savoir si une application générique répertorie les sources de données, les conducteurs ou les deux dépend souvent de l’utilisation d’un pilote basé sur DBMS ou de fichiers.  
  
 Les pilotes basés sur DBMS ont généralement besoin d’un ensemble complexe d’informations de connexion, telles que l’adresse réseau, le protocole réseau, le nom de base de données, et ainsi de suite. Le but d’une source de données est de cacher toutes ces informations. Par conséquent, le paradigme de source de données se prête à l’utilisation avec les pilotes basés sur DBMS. Une application peut afficher une liste de sources de données à l’utilisateur de deux façons. Il peut appeler **SQLDriverConnect** avec le mot clé **DSN** (Nom source de données) et aucune valeur associée; le Gestionnaire de pilote affichera une liste de noms de source de données. Si l’application veut le contrôle de l’apparence de la liste, elle appelle **SQLDataSources** pour récupérer une liste des sources de données disponibles et construit sa propre boîte de dialogue. Cette fonction est implémentée par le Driver Manager et peut être appelée avant que les pilotes ne soient chargés. L’application appelle alors une fonction de connexion et lui transmet le nom de la source de données choisie.  
  
 Si une source de données n’est pas spécifiée, la source de données par défaut indiquée par les informations du système est utilisée. (Pour plus d’informations, voir [Par défaut Subkey](../../../odbc/reference/install/default-subkey.md).) Si **SQLConnect** est appelé en utilisant un argument *ServerName* qui ne peut pas être trouvé, est un pointeur nul, ou est "DEFAULT", le gestionnaire de conducteur se connecte à la source de données par défaut. La source de données par défaut est également utilisée si la chaîne de connexion utilisée dans un appel à **SQLDriverConnect** ou **SQLBrowseConnect** contient le mot-clé **DSN** défini pour «DEFAULT» ou si la source de données spécifiée n’est pas trouvée. En outre, la source de données par défaut est utilisée si la chaîne de connexion qui est utilisée dans un appel à **SQLDriverConnect** ne contient pas le mot clé **DSN.**  
  
 Avec les pilotes basés sur des fichiers, il est possible d’utiliser un paradigme de fichier. Pour les données stockées sur l’ordinateur local, les utilisateurs savent souvent que leurs données se situent dans un fichier particulier, comme Employee.dbf. Au lieu de sélectionner une source de données inconnue, il est plus facile pour ces utilisateurs de sélectionner le fichier qu’ils connaissent. Pour mettre en œuvre cela, l’application appelle d’abord **SQLDrivers**. Cette fonction est implémentée par le Driver Manager et peut être appelée avant que les pilotes ne soient chargés. **SQLDrivers** retourne une liste de conducteurs disponibles; il renvoie également des valeurs pour les mots clés **FileUsage** et **FileExtns.** Le mot clé **FileUsage** explique si les pilotes basés sur des fichiers traitent les fichiers comme des tables, tout comme Xbase, ou comme des bases de données, tout comme Microsoft® Access. Le mot clé **FileExtns** répertorie les extensions de nom de fichier que le conducteur reconnaît, telles que .dbf pour un pilote Xbase. À l’aide de ces informations, l’application construit une boîte de dialogue par laquelle l’utilisateur choisit un fichier. Sur la base de l’extension du fichier choisi, l’application se connecte ensuite au conducteur en appelant **SQLDriverConnect** avec le mot clé **DRIVER.**  
  
 Rien n’empêche une application d’utiliser une source de données avec un pilote basé sur un fichier ou d’appeler **SQLDriverConnect** avec le mot clé **DRIVER** pour se connecter à un pilote basé sur DBMS. Voici plusieurs utilisations courantes du mot-clé **DRIVER** pour les conducteurs basés sur DBMS :  
  
-   **Ne pas créer de sources de données.** Par exemple, une application personnalisée peut utiliser un pilote et une base de données particuliers. Si le nom du conducteur et toutes les informations requises pour se connecter à la base de données sont codés en dur dans l’application, les utilisateurs n’ont pas à créer une source de données sur leur ordinateur pour exécuter l’application. Tout ce qu’ils doivent faire est d’installer l’application et le conducteur.  
  
     Un inconvénient de cette méthode est que l’application doit être recompilée et redistribuée si les informations de connexion changent. Si un nom source de données est codé en code dur dans l’application au lieu d’informations de connexion complètes, chaque utilisateur ne doit modifier que les informations contenues dans la source de données.  
  
-   **Accès à un DBMS particulier une seule fois.** Par exemple, une feuille de calcul qui récupère des données en appelant les fonctions ODBC peut contenir le mot clé **DRIVER** pour identifier un pilote particulier. Étant donné que le nom du conducteur est significatif pour tous les utilisateurs qui ont ce pilote, la feuille de calcul pourrait être passée parmi ces utilisateurs. Si la feuille de calcul contenait un nom de source de données, chaque utilisateur devrait créer la même source de données pour utiliser la feuille de calcul.  
  
-   **Parcourir le système pour toutes les bases de données accessibles à un pilote particulier.** Pour plus d’informations, voir [Connecting with SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md), plus tard dans cette section.
