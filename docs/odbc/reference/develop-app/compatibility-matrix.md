---
title: Matrice de compatibilité | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 273633532b9b9247ea7aa12fe90bfcc3c6f6bb81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083273"
---
# <a name="compatibility-matrix"></a>Matrice de compatibilité
Le tableau suivant décrit la compatibilité des types d’applications et de pilotes définis précédemment dans cette section.  
  
|Type d’application<br /><br /> et version|ODBC 32 bits<br /><br /> pilote *2. x*|ODBC *3. x*<br /><br /> pilote|Pilote ODBC 3,8|ISO et le pilote compatible avec les groupes ouverts|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|application 16 bits, toute version|Compatible|Compatible|Compatible|Compatible|  
|Application pure *2. x*|Compatible|Compatible|Compatible|Non compatible [3]|  
|Application pure *2. x* recompilée|Compatible|Compatible [1]|Compatible [1]|Non compatible [3]|  
|Application Unicode pure *2. x*|Compatible|Compatible [1]|Compatible [1]|Non compatible [3]|  
|Groupe ouvert pur et application conforme à la norme ISO|Non compatible|Compatible [2]|Compatible [2]|Compatible [2]|  
|Application 3,0 pure|Non compatible|Compatible|Compatible|Non compatible [4]|  
|Application 3,5 pure|Non compatible|Compatible|Compatible|Non compatible [4]|  
|Application pure 3,8 (ou version ultérieure)|Non compatible [5]|Non compatible [5]|Compatible|Non compatible [4]|  
|Application remplacée|Compatible|Compatible|Compatible|Non compatible [3]|  
  
 [1] l’application doit être recompilée à l’aide d’en-têtes ODBC 3,5 (ou version ultérieure) avec l’option UNICODE (s’il s’agit d’une application Unicode) et doit définir ODBCVER sur 0x0250.  
  
 [2] l’application doit être compilée à l’aide d’en-têtes ODBC 3,5 (ou version ultérieure) et être liée à ODBC Driver Manager. Elle doit également définir l’indicateur d’en-tête ODBC_STD.  
  
 [3] cette configuration peut potentiellement ne pas fonctionner, car il existe des fonctionnalités ODBC *2. x* qui ne sont pas dans les normes, telles que les signets.  
  
 [4] cette configuration peut potentiellement échouer, car il existe des fonctionnalités ODBC *3. x* qui ne sont pas dans les normes, telles que les signets.  
  
 [5] cette configuration peut potentiellement échouer, car il existe des fonctionnalités ODBC 3,8 qui ne sont pas dans les pilotes ODBC 2. x ou 3. x, comme les [types de données C](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)spécifiques au pilote dans ODBC.  
  
## <a name="driver-manager-compatibility"></a>Compatibilité du gestionnaire de pilotes  
 Une application ODBC 3,0 qui doit fonctionner avec toutes les versions du gestionnaire de pilotes doit effectuer les opérations suivantes au démarrage :  
  
-   Allouez un handle d’environnement.  
  
-   Affectez à l’attribut SQL_ATTR_ODBC_VERSION Environment la valeur SQL_OV_ODBC3_80. Si le gestionnaire de pilotes renvoie SQL_ERROR, le gestionnaire de pilotes est antérieur à 3,8. Réinitialisez SQL_ATTR_ODBC_VERSION sur SQL_OV_ODBC3 ou SQL_OV_ODBC2, selon le cas, pour qu’il corresponde au gestionnaire de pilotes.  
  
-   Allouez un handle de connexion.  
  
-   Établissez une connexion.  
  
-   Appelez SQLGetInfo pour SQL_DRIVER_ODBC_VER pour déterminer la version du pilote. Si le pilote est un pilote ODBC 3,8, vous pouvez utiliser des types C spécifiques au pilote. Dans le cas contraire, n’utilisez pas de types de données C spécifiques au pilote.  
  
 Notez qu’une application ODBC 3. x recompilée peut utiliser des fonctionnalités ODBC 3,8 autres que des types C spécifiques aux pilotes, sans spécifier SQL_OV_ODBC3_80 pour SQL_ATTR_ODBC_VERSION. Cela est similaire à une application ODBC 2. x recompilée à l’aide des fonctionnalités ODBC 3. x.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Utilisation de SQLCancelHandle dans une application compatible avec tous les gestionnaires de pilotes  
 Étant donné que la [fonction SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) n’est pas prise en charge dans les gestionnaires de pilotes qui ont été publiés avant Windows 7, une application ne peut pas être chargée dans les versions antérieures de Windows si elle appelle **SQLCancelHandle** directement. Pour travailler avec toutes les versions des gestionnaires de pilotes et utiliser **SQLCancelHandle** sur les nouvelles versions de Windows, une application doit appeler **SQLCancelHandle** indirectement en utilisant **LoadLibrary** et **GetProcAddress.**  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
