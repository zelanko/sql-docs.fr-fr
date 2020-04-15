---
title: Changements comportementaux et ODBC 3.x Pilotes (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d8343573261d74a6a0c652cf425b12da91f7cb0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292363"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>Changements de comportement et pilotes ODBC 3.x
L’attribut de l’environnement indique SQL_ATTR_ODBC_VERSION au conducteur s’il doit présenter un comportement ODBC *2.x* ou un comportement ODBC *3.x.* L’ensemble de l’attribut de l’environnement SQL_ATTR_ODBC_VERSION dépend de l’application. Les applications ODBC *3.x* doivent appeler **SQLSetEnvAttr** pour définir cet attribut après avoir appelé **SQLAllocHandle** pour allouer une poignée d’environnement et avant qu’ils appellent **SQLAllocHandle** pour allouer une poignée de connexion. S’ils ne le font pas, le gestionnaire de conducteur retourne SQLSTATE HY010 (erreur de séquence de fonction) sur ce dernier appel à **SQLAllocHandle**.  
  
> [!NOTE]  
>  Pour plus d’informations sur les changements de comportement et comment une application agit, voir [Behavioral Changes](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Les applications ODBC *2.x* et les applications ODBC *2.x* recompilées par les fichiers d’en-tête ODBC *3.x* n’appellent pas **SQLSetEnvAttr**. Cependant, ils appellent **SQLAllocEnv** au lieu de **SQLAllocHandle** pour allouer une poignée d’environnement. Par conséquent, lorsque la demande appelle **SQLAllocEnv** dans le gestionnaire de conducteur, le gestionnaire de conducteur appelle **SQLAllocHandle** et **SQLSetEnvAttr** dans le conducteur. Ainsi, les pilotes ODBC *3.x* peuvent toujours compter sur cet attribut étant défini.  
  
 Si une application conforme aux normes compilée avec le drapeau ODBC_STD compiler appelle **SQLAllocEnv** (ce qui peut se produire parce que **SQLAllocEnv** n’est pas déprécié dans ISO), l’appel est cartographié à **SQLAllocHandleStd** au moment de la compilation. Au moment de l’exécution, l’application appelle **SQLAllocHandleStd**. Le Driver Manager définit l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC3. Un appel à **SQLAllocHandleStd** équivaut à un appel à **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV et un appel à **SQLSetEnvAttr** pour mettre SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3.  
  
 Dans certaines architectures de conducteur, il est nécessaire que le conducteur apparaisse comme un conducteur ODBC *2.x* ou un pilote ODBC *3.x,* selon la connexion. Dans ce cas, le conducteur n’est peut-être pas un conducteur, mais une couche qui se trouve entre le gestionnaire de conducteur et un autre conducteur. Par exemple, il pourrait imiter un pilote, comme ODBC Spy. Dans un autre exemple, il pourrait agir comme une passerelle, comme EDA / SQL. Pour apparaître comme un conducteur ODBC *3.x,* un tel conducteur doit être en mesure d’exporter **SQLAllocHandle**, et d’apparaître comme un pilote ODBC *2.x,* doit être en mesure d’exporter **SQLAllocConnect**, **SQLAllocEnv**, et **SQLAllocStmt**. Lorsqu’un environnement, une connexion ou une déclaration doit être attribué, le gestionnaire de conducteur vérifie si ce conducteur exporte **SQLAllocHandle**. Comme le conducteur le fait, le gestionnaire de conducteur appelle **SQLAllocHandle** dans le conducteur. Si le conducteur travaille avec un conducteur ODBC *2.x,* le conducteur doit cartographier l’appel à **SQLAllocHandle** à **SQLAllocConnect**, **SQLAllocEnv**, ou **SQLAllocStmt**, le cas échéant. Il ne doit pas non plus ne rien faire avec **l’appel SQLSetEnvAttr** lorsqu’il se comporte comme un conducteur ODBC *2.x.*  
  
 Cette section contient les rubriques suivantes :  
  
-   [Type de données datetime](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [Compatibilité descendante des types de données C](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [Signets de longueur fixe](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo, prise en charge](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [Retour de SQL_NO_DATA](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [Appel de SQLSetPos pour insérer des données](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [Chargement par ordinal](../../../odbc/reference/appendixes/loading-by-ordinal.md)
