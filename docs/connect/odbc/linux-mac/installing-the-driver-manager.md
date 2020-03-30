---
title: Installation du Gestionnaire de pilote (pilote ODBC pour SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a276d44cd67bf7d2d4befd24edefa6ebdf0759a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79058787"
---
# <a name="installing-the-driver-manager"></a>Installation du Gestionnaire de pilotes
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article contient des instructions pour installer le Gestionnaire de pilotes unixODBC pour une utilisation avec toutes les versions du pilote Microsoft ODBC pour SQL Server sur Linux et macOS.  

> [!IMPORTANT]  
> Supprimez tous les packages de Gestionnaire de pilotes installés sur votre ordinateur avant d’installer le Gestionnaire de pilotes unixODBC. L’installation du Gestionnaire de pilotes unixODBC peut entraîner une défaillance d’un Gestionnaire de pilotes existant.  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-13-131-and-17"></a>Installation du Gestionnaire de pilotes pour Microsoft ODBC Driver 13, 13.1 et 17
La dépendance de gestionnaire de pilote est automatiquement résolue par le système de gestion des packages quand vous installez Microsoft ODBC Driver 13, 13.1 ou 17 pour SQL Server sur Linux ou macOS en suivant les instructions contenues dans les articles suivants :

- [Installation de Microsoft ODBC Driver for SQL Server sur Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installation de Microsoft ODBC Driver for SQL Server sur macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Installation du Gestionnaire de pilotes pour Microsoft ODBC Driver 11 for SQL Server  

(SUSE et Red Hat Linux uniquement).

**Utilisation du script d’installation**  
  
> [!IMPORTANT]  
> Ces instructions font référence à `msodbcsql-11.0.2270.0.tar.gz`, à savoir le fichier d’installation pour Red Hat Linux. Si vous installez la préversion pour SUSE Linux, le nom du fichier est `msodbcsql-11.0.2260.0.tar.gz`.  

Pour installer le Gestionnaire de pilotes  
  
1.  Assurez-vous de disposer d’une autorisation d’accès à la racine.  
  
2.  Accédez au répertoire où le téléchargement de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a placé le fichier nommé `msodbcsql-11.0.2270.0.tar.gz`. Assurez-vous de disposer du fichier \*.tar.gz correspondant à votre version de Linux. Pour extraire les fichiers, exécutez la commande suivante : **tar xvzf msodbcsql-11.0.2270.0.tar.gz**.  

3.  Accédez au répertoire `msodbcsql-11.0.2270.0`, où devrait se trouver un fichier nommé `build_dm.sh`. Vous pouvez exécuter `build_dm.sh` pour installer le Gestionnaire de pilotes unixODBC.

4.  Pour afficher la liste des options disponibles, exécutez la commande suivante : **./build_dm.sh --help**.  
  
5.  Quand vous êtes prêt pour l’installation et si votre ordinateur peut accéder à un site externe par le biais de FTP, exécutez la commande suivante : **./build_dm.sh**.

Si votre ordinateur ne peut pas accéder à un site externe par le biais de FTP, obtenez `unixODBC-2.3.0.tar.gz`. Vous pouvez obtenir `unixODBC-2.3.0.tar.gz` à partir de [http://www.unixodbc.org](http://www.unixodbc.org/). Cliquez sur le lien **Télécharger** sur le côté gauche de la page pour accéder à la page de téléchargement. Cliquez ensuite sur le lien approprié pour télécharger unixODBC-2.3.0 (et non unixODBC-2.3.1). unixODBC-2.3.1 n’est pas pris en charge avec cette version de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Exécutez la commande suivante pour commencer l’installation du Gestionnaire de pilotes unixODBC : **./build_dm.sh --download-url=file://unixODBC-2.3.0.tar.gz**.  

6.  Tapez **OUI** pour poursuivre la décompression des fichiers. Cette partie du processus peut prendre jusqu’à cinq minutes.  

7.  Une fois le script terminé, suivez les instructions à l’écran pour installer le Gestionnaire de pilotes unixODBC.

Vous êtes maintenant prêt à installer le pilote. Pour plus d’informations, consultez les instructions d’installation du pilote ODBC pour [Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) ou [macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).

**Installation manuelle**

Si le script d’installation ne peut pas se terminer, configurez et générez le Gestionnaire de pilotes approprié vous-même.

1.  Supprimez toute version antérieure installée d’unixODBC (par exemple unixODBC 2.2.11). Sur Red Hat Enterprise Linux 5 ou 6, exécutez la commande suivante : **yum remove unixODBC**. Sur SUSE Linux Enterprise, **zypper supprimer unixODBC**.  
  
2.  Accédez à [http://www.unixodbc.org](http://www.unixodbc.org/). Cliquez sur le lien **Télécharger** sur le côté gauche de la page pour accéder à la page de téléchargement. Cliquez ensuite sur le lien approprié pour enregistrer le fichier unixODBC-2.3.0.tar.gz sur votre ordinateur. UnixODBC-2.3.1 n’est pas pris en charge avec cette version de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
3.  Sur votre ordinateur Linux, exécutez la commande : **tar xvzf unixODBC-2.3.0.tar.gz**.  
  
4.  Accédez au répertoire unixODBC-2.3.0.  
  
5.  Dans l’invite de commandes, exécutez la commande : **CPPFLAGS="-DSIZEOF_LONG_INT=8"** .  
  
6.  À l’invite de commandes, exécutez la commande : **export CPPFLAGS**.  
  
7.  À l’invite de commandes, exécutez la commande : **"./configure --prefix=/usr --libdir=/usr/lib64 --sysconfdir=/etc --enable-gui=no --enable-drivers=no --enable-iconv --with-iconv-char-enc=UTF8 --with-iconv-ucode-enc=UTF16LE"** .  
  
8.  À l’invite de commandes (connecté en tant que racine), exécutez la commande suivante : **make**.  
  
9. À l’invite de commandes (connecté en tant que racine), exécutez la commande suivante : **make install**.  

Vous êtes maintenant prêt à installer le pilote. Pour plus d’informations, consultez les instructions d’installation du pilote ODBC pour [Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) ou [macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).
  
## <a name="see-also"></a>Voir aussi

- [Installation de Microsoft ODBC Driver for SQL Server sur Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installation de Microsoft ODBC Driver for SQL Server sur macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
- [Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)
