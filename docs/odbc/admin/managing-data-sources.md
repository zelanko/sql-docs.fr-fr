---
title: Gestion des sources de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9dc741321894ae69a9ffb59738576a01d47628f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901660"
---
# <a name="managing-data-sources"></a>Gestion des sources de données
Une fois que vous avez installé un pilote ODBC à partir du programme d’installation du pilote, vous pouvez définir une ou plusieurs sources de données pour celui-ci. Le nom de la source de données (DSN) doit fournir une description unique des données ; par exemple, *paie* ou *comptes fournisseurs*. Les sources de données utilisateur et système définies pour tous les pilotes actuellement installés sont répertoriées dans les onglets **DSN utilisateur** ou **DSN système** de la boîte de dialogue **administrateur de sources de données ODBC** . Les sources de données de fichier dans un répertoire donné sont répertoriées sous l’onglet **fichier DSN** . le répertoire à afficher est entré dans la zone **regarder dans** de l’onglet **DSN de fichier** .  
  
> [!NOTE]  
>  Pour gérer une source de données qui se connecte à un pilote 32 bits sous la plateforme 64 bits, utilisez c:\windows\sysWOW64\odbcad32.exe. Pour gérer une source de données qui se connecte à un pilote 64 bits, utilisez c:\windows\system32\odbcad32.exe. Dans les **Outils d’administration** sur un système d’exploitation Windows 8 64 bits, il existe des icônes pour la boîte de dialogue administrateur de la **source de données ODBC** 32 bits et 64 bits.  
  
 Si vous utilisez l’odbcad32. exe 64 bits pour configurer ou supprimer un nom de source de fichier qui se connecte à un pilote 32 bits, par exemple, le **pilote fait Microsoft Access (\*. mdb)**, le message d’erreur suivant s’affiche :  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Pour résoudre cette erreur, utilisez le fichier odbcad32. exe 32 bits pour configurer ou supprimer le DSN.  
  
 Une source de données associe un pilote ODBC particulier aux données auxquelles vous souhaitez accéder par le biais de ce pilote. Par exemple, vous pouvez créer une source de données pour utiliser le pilote ODBC dBASE pour accéder à un ou plusieurs fichiers dBASE trouvés dans un répertoire spécifique sur votre disque dur ou sur un lecteur réseau. À l’aide de l’administrateur de la source de données ODBC, vous pouvez ajouter, modifier et supprimer des sources de données, comme décrit dans le tableau suivant.  
  
|Action|Description|  
|------------|-----------------|  
|Ajout de sources de données|Il est possible d’ajouter plusieurs sources de données, chacune associant un pilote à des données auxquelles vous souhaitez accéder à l’aide de ce pilote. Attribuez à chaque source de données un nom qui identifie de façon unique cette source de données. Par exemple, si vous créez une source de données pour un ensemble de fichiers dBASE qui contiennent des informations client, vous pouvez nommer la source de données « clients ». En général, les applications affichent les noms des sources de données que les utilisateurs peuvent choisir.<br /><br /> L’ajout d’une source de données de fichier diffère légèrement de l’ajout de sources de données utilisateur ou système. Pour plus d’informations, consultez le fichier d’aide de l’administrateur de la source de données ODBC.|  
|Modification des sources de données|Selon vos besoins, il peut s’avérer nécessaire de reconfigurer les sources de données. Vous pouvez réinitialiser les options en cliquant sur **configurer** dans la boîte de dialogue Configuration de n’importe quel pilote.|  
|Suppression de sources de données|Cliquez sur **supprimer** après avoir sélectionné une source de données.|  
  
 Pour plus d’informations sur les sources de données de fichier, consultez [connexion à l’aide de sources de données de fichier](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) ou de la [fonction SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrateur des sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md)
