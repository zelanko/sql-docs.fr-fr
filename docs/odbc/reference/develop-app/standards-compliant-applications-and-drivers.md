---
description: Applications et pilotes conformes aux normes
title: Applications et pilotes conformes aux normes | Microsoft Docs
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
ms.openlocfilehash: e6733afa5281f86d8dd425e6157832ee0680d34b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476381"
---
# <a name="standards-compliant-applications-and-drivers"></a>Applications et pilotes conformes aux normes
Une application ou un pilote conforme aux normes est un pilote conforme à la spécification Open Group IAO « Gestion des données : interface de niveau d’appel SQL (CLI) » et l’interface de niveau d’appel ISO/IEC 9075-3:1995 (E) (SQL/CLI).  
  
 ODBC *3. x* garantit les fonctionnalités suivantes :  
  
-   Une application écrite dans les spécifications Open Group et ISO CLI fonctionne avec un pilote ODBC *3. x* ou un pilote conforme aux normes lorsqu’elle est compilée avec les fichiers d’en-tête ODBC *3. x* et est liée aux bibliothèques ODBC *3. x* , et lorsqu’elle accède au pilote par le biais du gestionnaire de pilotes ODBC *3. x* .  
  
-   Un pilote écrit dans les spécifications Open Group et ISO CLI fonctionne avec une application ODBC *3. x* ou une application conforme aux normes lorsqu’elle est compilée avec les fichiers d’en-tête ODBC *3. x* et est liée aux bibliothèques ODBC *3. x* , et lorsque l’application accède au pilote par le biais du gestionnaire de pilotes ODBC *3. x* .  
  
 Les applications et les pilotes conformes aux normes sont compilés avec l’indicateur de compilation ODBC_STD.  
  
 Les applications conformes aux normes présentent le comportement suivant :  
  
-   Si une application conforme aux normes appelle **SQLAllocEnv** (ce qui peut se produire parce que **SQLAllocEnv** est une fonction valide dans le groupe Open et l’interface CLI ISO), l’appel est mappé à **SQLAllocHandleStd** au moment de la compilation. Par conséquent, au moment de l’exécution, l’application appelle **SQLAllocHandleStd**. Au cours du traitement de cet appel, le gestionnaire de pilotes définit l’attribut d’environnement SQL_ATTR_ODBC_VERSION sur SQL_OV_ODBC3. Un appel à **SQLAllocHandleStd** est équivalent à un appel à **SQLAllocHandle** avec un *comme HandleType* de SQL_HANDLE_ENV et un appel à **SQLSetEnvAttr** pour définir SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3.  
  
-   Si une application conforme aux normes appelle **SQLBindParam** (ce qui peut se produire parce que **SQLBindParam** est une fonction valide dans le groupe Open et l’interface CLI ISO), le gestionnaire de pilotes ODBC *3. x* mappe l’appel à l’appel équivalent dans **SQLBindParameter**. (Voir le [mappage SQLBindParam](../../../odbc/reference/appendixes/sqlbindparam-mapping.md) dans l’annexe G : instructions relatives aux pilotes pour la compatibilité descendante.)  
  
-   Pour aligner avec l’interface CLI ISO, les fichiers d’en-tête ODBC *3. x* contiennent des alias pour les types d’informations utilisés dans les appels à **SQLGetInfo**. Une application conforme aux normes peut utiliser ces alias au lieu des types d’informations ODBC *3. x* . Pour plus d’informations, consultez la rubrique suivante, [fichiers d’en-tête](../../../odbc/reference/develop-app/header-files.md).  
  
-   Une application conforme aux normes doit vérifier que toutes les fonctionnalités qu’elle prend en charge sont prises en charge dans le pilote qu’elle utilisera. La définition de l’attribut d’instruction SQL_ATTR_CURSOR_SCROLLABLE sur SQL_SCROLLABLE et la définition de l’attribut d’instruction SQL_ATTR_CURSOR_SENSITIVITY sur SQL_INSENSITIVE ou SQL_SENSITIVE sont des fonctionnalités disponibles en tant que fonctionnalités facultatives dans les normes, mais qui ne sont pas incluses dans le niveau principal ODBC *3. x* et qui, par conséquent, ne sont pas prises en charge par tous les pilotes ODBC *3. x* . Si une application conforme aux normes utilise ces fonctionnalités, elle doit vérifier que le pilote qu’elle utilisera les prend en charge.
