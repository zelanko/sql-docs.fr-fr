---
title: Développer des applications pour SQL Server sur Linux | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.custom: sql-linux
ms.suite: sql
ms.technology: linux
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.openlocfilehash: c50b0ad1798f161d945a54e0e9a080a04a6eca05
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712971"
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Comment commencer à développer des applications pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Vous pouvez créer des applications qui se connectent à utilisent SQL Server sur Linux à partir d’une variété de langages de programmation, tels que c#, Java, Node.js, PHP, Python, Ruby et C++. Vous pouvez également utiliser les frameworks web et les mapping objet-relationnel (en anglais object-relational mapping ou ORM) les plus courants.

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> Ces mêmes options de développement vous permettent également de cibler SQL Server sur d'autres plates-formes. Les applications peuvent cibler SQL Server fonctionnant sur site ou dans le Cloud, sous Linux, sous Windows ou via Docker sur macOS. Vous pouvez également cibler la base de données SQL Azure et Azure SQL Data Warehouse

## <a name="try-the-tutorials"></a>Suivez les didacticiels

La meilleure façon de démarrer et de créer des applications avec SQL Server est de l'essayer par vous-même.

- Voir le [didacticiels de démarrage](http://aka.ms/sqldev).
- Sélectionnez votre langue et votre plateforme de développement.
- Essayez les exemples de code.

> [!TIP]
> Si vous souhaitez développer pour SQL Server sur Docker, examinons le **macOS** didacticiels.

## <a name="create-new-applications"></a>Créer des applications

Si vous créez une nouvelle application, jetez un coup d'oeil à la liste des [bibliothèques de connectivité](sql-server-linux-develop-connectivity-libraries.md) pour obtenir un résumé des connecteurs et des frameworks populaires disponibles pour différents langages de programmation.

## <a name="use-existing-applications"></a>Utiliser des applications existantes

Si vous avez une application de base de données existante, vous pouvez simplement modifier sa chaîne de connexion à SQL Server sur Linux cible. Veillez à en savoir plus sur la [problèmes connus](sql-server-linux-release-notes.md) dans SQL Server sur Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Utiliser les outils SQL existants sous Windows avec SQL Server sur Linux

Les outils qui exécutent actuellement sur Windows tels que SSMS, SSDT et PowerShell, fonctionnent également avec SQL Server sur Linux. Bien qu'ils ne fonctionnent pas nativement sous Linux, vous pouvez quand même gérer les instances SQL Server distantes sous Linux. 

Consultez les rubriques suivantes pour plus d’informations :

- [SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note]
> Assurez-vous d'utiliser les dernières versions de ces outils pour une expérience optimale.

## <a name="use-new-sql-tools-for-linux"></a>Utiliser les nouveaux outils SQL pour Linux

Vous pouvez utiliser la nouvelle [extension mssql](https://aka.ms/mssql-marketplace) pour [Visual Studio Code](https://code.visualstudio.com) sous Linux, MacOS et Windows. Pour une marche à suivre étape par étape, consultez le tutoriel suivant :

- [Utilisez Visual Studio Code](sql-server-linux-develop-use-vscode.md)

Vous pouvez également utiliser de nouveaux outils de ligne de commande natifs pour Linux. Ces outils comprennent les suivants :

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Étapes suivantes

Pour démarrer, installez SQL Server sur Linux en suivant l'une des sections de démarrage rapide suivantes :

- [Installation sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)
