---
title: Matrice de compatibilité (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0406599e1657a900d1669861572ff13834cec670
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307452"
---
# <a name="compatibility-matrix"></a>Matrice de compatibilité
Le tableau suivant décrit la compatibilité des types d’applications et de pilotes définis précédemment dans cette section.  
  
|Type d'application<br /><br /> et la version|ODBC 32 bits<br /><br /> *2.x* conducteur|ODBC *3.x*<br /><br /> pilote|Pilote ODBC 3.8|Pilote ISO et Open Group-conforme|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|Application 16 bits, n’importe quelle version|Compatible|Compatible|Compatible|Compatible|  
|Application *Pure 2.x*|Compatible|Compatible|Compatible|Non compatible[3]|  
|Application pure *2.x* recompilée|Compatible|Compatible[1]|Compatible[1]|Non compatible[3]|  
|Application Pure *2.x* Unicode|Compatible|Compatible[1]|Compatible[1]|Non compatible[3]|  
|Pure Open Group et application conforme à l’ISO|Non compatible|Compatible[2]|Compatible[2]|Compatible[2]|  
|Application Pure 3.0|Non compatible|Compatible|Compatible|Non compatible[4]|  
|Application Pure 3.5|Non compatible|Compatible|Compatible|Non compatible[4]|  
|Application pure 3.8 (ou plus)|Non compatible [5]|Non compatible [5]|Compatible|Non compatible [4]|  
|Application remplacée|Compatible|Compatible|Compatible|Non compatible[3]|  
  
 [1] L’application doit recomposer à l’aide d’en-têtes ODBC 3.5 (ou plus) avec l’option UNICODE (s’il s’agit d’une application Unicode) et doit définir ODBCVER à 0x0250.  
  
 [2] L’application doit compiler à l’aide d’ODBC 3.5 (ou plus) d’en-têtes et un lien avec le gestionnaire de conducteur ODBC. Il doit également définir le drapeau d’en-tête ODBC_STD.  
  
 Cette configuration peut potentiellement ne pas fonctionner parce qu’il y a des fonctionnalités dans ODBC *2.x* qui ne sont pas dans les normes, telles que les signets.  
  
 Cette configuration peut potentiellement ne pas fonctionner parce qu’il y a des fonctionnalités dans ODBC *3.x* qui ne sont pas dans les normes, telles que les signets.  
  
 Cette configuration peut potentiellement échouer parce qu’il y a des fonctionnalités dans ODBC 3.8 qui ne sont pas dans ODBC 2.x ou 3.x pilotes, tels que les types de données C spécifiques au conducteur [dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Compatibilité de gestionnaire de conducteur  
 Une application ODBC 3.0 qui doit fonctionner avec toutes les versions Driver Manager doit faire ce qui suit sur le démarrage:  
  
-   Allouer une poignée d’environnement.  
  
-   Définissez l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC3_80. Si le gestionnaire de conducteur revient SQL_ERROR, le gestionnaire de conducteur a plus de 3,8 ans. Réinitialisez SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3 ou SQL_OV_ODBC2, le cas échéant, pour correspondre au gestionnaire de conducteur.  
  
-   Allouer une poignée de connexion.  
  
-   Faites une connexion.  
  
-   Appelez SQLGetInfo pour SQL_DRIVER_ODBC_VER pour déterminer la version du conducteur. Si le conducteur est un conducteur ODBC 3.8, vous pouvez utiliser des types C spécifiques au conducteur. Sinon, n’utilisez pas de types de données C spécifiques au conducteur.  
  
 Notez qu’une application 3.x ODBC recompilée peut utiliser des fonctionnalités ODBC 3.8 autres que les types C spécifiques au conducteur sans spécifier SQL_OV_ODBC3_80 pour SQL_ATTR_ODBC_VERSION. Ceci est similaire à une application 2.x ODBC recompilée utilisant les fonctionnalités ODBC 3.x.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Utilisation de SQLCancelHandle dans une application compatible avec tous les gestionnaires de pilotes  
 Étant donné que [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md) n’est pas pris en charge dans Driver Managers qui ont été libérés avant Windows 7, une application ne peut pas être chargée dans les anciennes versions de Windows si elle appelle **SQLCancelHandle** directement. Pour travailler avec toutes les versions de Driver Managers et utiliser **SQLCancelHandle** sur les nouvelles versions de Windows, une application devrait appeler **SQLCancelHandle** indirectement en utilisant **LoadLibrary** et **GetProcAddress.**  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
