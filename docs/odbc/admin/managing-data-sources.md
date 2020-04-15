---
title: Gestion des sources de données (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5069ac9a5babc3071c52d73d5b56b21729a5d8a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307210"
---
# <a name="managing-data-sources"></a>Gestion des sources de données
Une fois que vous avez installé un pilote ODBC du programme d’installation du pilote, vous pouvez définir une ou plusieurs sources de données pour cela. Le nom de source de données (DSN) doit fournir une description unique des données; par exemple, *la paie* ou *les comptes payables*. Les sources de données utilisateur et système définies pour tous les pilotes actuellement installés sont répertoriées dans les onglets **DSN** utilisateur ou **système** de la boîte de dialogue **ODBC Data Source Administrator.** Les sources de données de fichiers dans un répertoire donné sont énumérées dans **l’onglet DSN de fichier** ; l’annuaire à montrer est entré dans la boîte **Look in** box dans **l’onglet Fichier DSN.**  
  
> [!NOTE]  
>  Pour gérer une source de données qui se connecte à un pilote 32 bits sous plate-forme 64 bits, utilisez c: 'windows’sysWOW64'odbcad32.exe. Pour gérer une source de données qui se connecte à un pilote 64 bits, utilisez c: 'windows’system32'odbcad32.exe. Dans **les outils administratifs** sur un système d’exploitation Windows 8 64 bits, il existe des icônes pour la boîte de dialogue 32 bits et 64 bits **ODBC Data Source Administrator.**  
  
 Si vous utilisez l’odbcad32.exe 64 bits pour configurer ou supprimer une DSN qui se connecte à un pilote 32 bits, par exemple, **Driver do Microsoft Access (\*.mdb)**, vous recevrez le message d’erreur suivant :  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Pour résoudre cette erreur, utilisez l’odbcad32.exe 32 bits pour configurer ou supprimer le DSN.  
  
 Une source de données associe un pilote ODBC particulier aux données auxquelles vous souhaitez accéder par l’intermédiaire de ce conducteur. Par exemple, vous pouvez créer une source de données pour utiliser le pilote ODBC dBASE pour accéder à un ou plusieurs fichiers DBASE trouvés dans un répertoire spécifique sur votre disque dur ou un lecteur réseau. À l’aide de l’administrateur de source de données ODBC, vous pouvez ajouter, modifier et supprimer les sources de données, telles que décrites dans le tableau suivant.  
  
|Action|Description|  
|------------|-----------------|  
|Ajout de sources de données|Il est possible d’ajouter plusieurs sources de données, chacune associant un pilote avec certaines données auxquelles vous souhaitez accéder en utilisant ce pilote. Donnez à chaque source de données un nom qui identifie uniquement cette source de données. Par exemple, si vous créez une source de données pour un ensemble de fichiers DBASE qui contiennent des informations clients, vous pouvez nommer la source de données « Clients ». Les applications affichent généralement les noms de source de données parmi les utilisateurs.<br /><br /> L’ajout d’une source de données de fichiers est légèrement différent de l’ajout de sources de données utilisateur ou système. Pour plus d’informations, consultez le fichier d’aide de l’administrateur de source de données ODBC.|  
|Modification des sources de données|Selon vos exigences, vous pourriez trouver nécessaire de reconfigurer les sources de données. Vous pouvez réinitialiser les options en cliquant **sur Configurer** dans n’importe quelle boîte de dialogue de configuration du pilote.|  
|Suppression des sources de données|Cliquez **sur Supprimer** après la sélection d’une source de données.|  
  
 Pour plus d’informations sur les sources de données de fichiers, voir [Connecting Using File Data Sources](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) ou la fonction [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrateur des sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md)
