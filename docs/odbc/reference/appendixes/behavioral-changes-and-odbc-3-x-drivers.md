---
title: Changements de comportement et pilotes ODBC 3.x | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e386aa60489fe3edb2caac3cb49ebad263ffdfac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026624"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Changements de comportement et pilotes ODBC 3.x
L’attribut d’environnement SQL_ATTR_ODBC_VERSION indique au pilote si elle doit présenter ODBC 2. *x* comportement ou ODBC 3 *.x* comportement. Configuration de l’attribut d’environnement SQL_ATTR_ODBC_VERSION dépend de l’application. ODBC 3 *.x* les applications doivent appeler **SQLSetEnvAttr** pour définir cet attribut après qu’ils appellent **SQLAllocHandle** pour allouer un handle d’environnement et avant d’appeler  **SQLAllocHandle** pour allouer un handle de connexion. Si elles ne le faites pas, le Gestionnaire de pilotes retourne SQLSTATE HY010 (erreur de séquence de fonction) sur le dernier appel à **SQLAllocHandle**.  
  
> [!NOTE]  
>  Pour plus d’informations sur les changements de comportement et de la façon dont une application fonctionne, consultez [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 ODBC 2. *x* applications et ODBC 2. *x* applications recompilées avec l’ODBC 3 *.x* n’appellent pas de fichiers d’en-tête **SQLSetEnvAttr**. Toutefois, ils appellent **SQLAllocEnv** au lieu de **SQLAllocHandle** pour allouer un handle d’environnement. Par conséquent, lorsque l’application appelle **SQLAllocEnv** dans le Gestionnaire de pilotes, le Gestionnaire de pilotes appelle **SQLAllocHandle** et **SQLSetEnvAttr** dans le pilote. Par conséquent, ODBC 3 *.x* pilotes peuvent toujours compter sur cet attribut est défini.  
  
 Si une application conforme aux normes compilé avec l’indicateur de compilation ODBC_STD appels **SQLAllocEnv** (qui peut se produire car **SQLAllocEnv** n’est pas déconseillée dans la norme ISO), l’appel est mappé à  **SQLAllocHandleStd** au moment de la compilation. À l’exécution, l’application appelle **SQLAllocHandleStd**. Le Gestionnaire de pilotes définit l’attribut d’environnement SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3. Un appel à **SQLAllocHandleStd** équivaut à un appel à **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV et un appel à **SQLSetEnvAttr** à la valeur SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3.  
  
 Dans certaines architectures de pilote, il est nécessaire pour le pilote à apparaissent sous la forme soit un ODBC 2. *x* pilote ou un ODBC 3 *.x* pilote, en fonction de la connexion. Le pilote dans ce cas en fait peut-être pas un pilote, mais une couche qui se trouve entre le Gestionnaire de pilotes et un autre pilote. Par exemple, il peut imiter un pilote, telles que ODBC Spy. Dans un autre exemple, il peut agir en tant que passerelle, tel que EDA/SQL. Apparaisse comme un ODBC 3 *.x* pilote, ce type de pilote doit être en mesure d’exporter **SQLAllocHandle**et apparaissent sous la forme d’une API ODBC 2. *x* pilote, doit être en mesure d’exporter **SQLAllocConnect**, **SQLAllocEnv**, et **SQLAllocStmt**. Lorsqu’un environnement, une connexion ou une instruction doit être allouée, le Gestionnaire de pilotes vérifie si ce pilote exporte **SQLAllocHandle**. Étant donné que le pilote est le cas, les appels du Gestionnaire de pilotes **SQLAllocHandle** dans le pilote. Si le pilote ne fonctionne pas avec un ODBC 2. *x* pilote, le pilote doit mapper l’appel à **SQLAllocHandle** à **SQLAllocConnect**, **SQLAllocEnv**, ou  **SQLAllocStmt**, le cas échéant. Il doit également effectuer rien avec le **SQLSetEnvAttr** appeler lorsque qui se comporte comme un ODBC 2. *x* pilote.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Type de données datetime](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Compatibilité descendante des types de données C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Signets de longueur fixe](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo, prise en charge](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Retour de SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Appel de SQLSetPos pour insérer des données](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Chargement par ordinal](../../../odbc/reference/appendixes/loading-by-ordinal.md)
