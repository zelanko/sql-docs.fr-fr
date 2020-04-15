---
title: Applications et pilotes conformes aux normes ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b4daf2e777b20b1b84c090757d0d84796a4cae1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299716"
---
# <a name="standards-compliant-applications-and-drivers"></a>Applications et pilotes conformes aux normes
Une application ou un pilote conforme aux normes est conforme à la spécification CAE open Group «Data Management: SQL Call-Level Interface (CLI) et à l’ISO/IEC 9075-3:1995 (E) Interface de niveau d’appel (SQL/CLI).  
  
 ODBC *3.x* garantit les fonctionnalités suivantes :  
  
-   Une application écrite aux spécifications Open Group et ISO CLI fonctionnera avec un pilote ODBC *3.x* ou un pilote conforme aux normes lorsqu’elle sera compilée avec les fichiers d’en-tête ODBC *3.x* et reliée aux bibliothèques ODBC *3.x,* et lorsqu’elle accède au pilote par l’intermédiaire du gestionnaire de conducteur ODBC *3.x.*  
  
-   Un pilote écrit selon les spécifications Open Group et ISO CLI travaillera avec une application ODBC *3.x* ou une application conforme aux normes lorsqu’il sera compilé avec les fichiers d’en-tête ODBC *3.x* et lié aux bibliothèques ODBC *3.x,* et lorsque l’application accède au pilote par l’intermédiaire du gestionnaire de conducteur ODBC *3.x.*  
  
 Les applications conformes aux normes et les pilotes sont compilés avec le drapeau de compilation ODBC_STD.  
  
 Les applications conformes aux normes présentent le comportement suivant :  
  
-   Si une application conforme aux normes appelle **SQLAllocEnv** (ce qui peut se produire parce que **SQLAllocEnv** est une fonction valide dans le groupe ouvert et ISO CLI), l’appel est cartographié à **SQLAllocHandleStd** au moment de la compilation. Par conséquent, à l’heure d’exécution, l’application appelle **SQLAllocHandleStd**. Au cours du traitement de cet appel, le Gestionnaire de conducteur définit l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC3. Un appel à **SQLAllocHandleStd** équivaut à un appel à **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV et un appel à **SQLSetEnvAttr** pour mettre SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3.  
  
-   Si une application conforme aux normes appelle **SQLBindParam** (ce qui peut se produire parce que **SQLBindParam** est une fonction valide dans le groupe ouvert et ISO CLI), l’ODBC *3.x* Driver Manager cartographie l’appel à l’appel équivalent dans **SQLBindParameter**. (Voir [SQLBindParam Mapping](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) in Appendix G: Driver Guidelines for Backward Compatibility.)  
  
-   Pour s’aligner sur l’ISO CLI, les fichiers d’en-tête ODBC *3.x* contiennent des alias pour les types d’informations utilisés dans les appels à **SQLGetInfo**. Une application conforme aux normes peut utiliser ces alias au lieu des types d’information ODBC *3.x.* Pour plus d’informations, voir le sujet suivant, [Header Files](../../../odbc/reference/develop-app/header-files.md).  
  
-   Une application conforme aux normes doit vérifier que toutes les fonctionnalités qu’elle prend en charge sont prises en charge dans le conducteur avec lequel elle fonctionnera. La définition de l’attribut SQL_ATTR_CURSOR_SCROLLABLE énoncé à SQL_SCROLLABLE et l’établissement de l’attribut de l’énoncé de SQL_ATTR_CURSOR_SENSITIVITY à SQL_INSENSITIVE ou SQL_SENSITIVE sont des capacités qui sont disponibles en tant que fonctionnalités facultatives dans les normes, mais qui ne sont pas incluses dans le niveau ODBC *3.x* Core et qui, par conséquent, pourraient ne pas être prises en charge par tous les pilotes ODBC *3.x.* Si une application conforme aux normes utilise ces capacités, elle doit vérifier que le conducteur avec lequel il travaillera les prend en charge.
