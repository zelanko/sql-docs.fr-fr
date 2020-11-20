---
title: Installer le CLR personnalisé Python
description: Découvrez comment installer un CLR personnalisé Python pour SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 09/20/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2a37b086804a8fabe3719db0744b49345d69e6b8
ms.sourcegitcommit: 2bf83972036bdbe6a039fb2d1fc7b5f9ca9589d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674137"
---
# <a name="install-a-python-custom-runtime-for-sql-server"></a>Installer un CLR personnalisé Python pour SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Cet article explique comment installer un CLR personnalisé pour l’exécution de scripts Python avec SQL Server. Le runtime personnalisé utilise une technologie d’extension de langage reposant sur un framework d’extensibilité pour l’exécution de code externe. Le CLR personnalisé pour Python peut être utilisé dans les scénarios suivants :

+ Une installation de SQL Server avec l’infrastructure d’extensibilité.

+ Une installation de Machine Learning Services avec SQL Server 2019. L’extension de langage peut être utilisée avec [Machine Learning Services SQL Server](../sql-server-machine-learning-services.md) après avoir effectué des étapes de configuration supplémentaires.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

> [!NOTE]
> Cet article explique comment installer un CLR personnalisé pour l’exécution de scripts Python sur Windows. Pour installer sur Linux, consultez [Installer un CLR personnalisé Python pour SQL Server sur Linux](custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true).

## <a name="pre-install-checklist"></a>Liste de contrôle avant l’installation

Avant d’installer un CLR personnalisé Python, installez les éléments suivants :

+ [Mise à jour cumulative 3 de SQL Server 2019 pour Windows](../../database-engine/install-windows/install-sql-server.md).

+ [Extensions de langage SQL Server sur Windows avec l’infrastructure d’extensibilité](../../language-extensions/install/windows-java.md).

+ [Python 3.7]( https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-windows"></a>Ajouter des extensions de langage SQL Server pour Windows

> [!NOTE]
> Si vous avez Machine Learning Services installé sur SQL Server 2019, l’infrastructure d’extensibilité est déjà installée et vous pouvez ignorer cette étape.

Les extensions de langage utilisent l’infrastructure d’extensibilité pour exécuter du code externe. L’exécution du code est isolée des processus du moteur de base, mais entièrement intégrée à l’exécution des requêtes SQL Server.

1. Démarrez l’Assistant Installation de SQL Server 2019.
  
1. Sous l’onglet **Installation**, sélectionnez **Nouvelle installation autonome de SQL Server ou ajout de fonctionnalités à une installation existante**.
    
    ![Installation de SQL Server 2019 CU3 ou version ultérieure](../install/media/2019setup-installation-page-mlsvcs.png) 

1. Dans la page **Sélection de fonctionnalités** , sélectionnez les options suivantes :
  
    - **Services Moteur de base de données**
  
        Pour utiliser les extensions de langage avec SQL Server, vous devez installer une instance du moteur de base de données. Vous pouvez utiliser l’instance par défaut ou une instance nommée.
  
    - **Machine Learning Services et extensions de langage**
   
       Sélectionnez **Machine Learning Services et extensions de langage**. Il n’est pas nécessaire de sélectionner Python.

    ![Fonctionnalités d’installation de SQL Server 2019 CU3 ou versions ultérieures](../install/media/sql-feature-selection.png) 

1. Dans la page **Prêt pour l’installation**, vérifiez que ces sélections sont incluses, puis choisissez **Installer**.
  
    + Services Moteur de base de données
    + Machine Learning Services et extensions de langage

1. Si vous êtes invité à redémarrer l’ordinateur après l’installation, faites-le dès à présent. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d'informations, consultez [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).


## <a name="install-python-37"></a>Installez Python 3.7 

Installez [Python 3.7]( https://www.python.org/downloads/release/python-379/) et ajoutez-le au PATH.

![Ajoutez Python 3.7 au chemin d'accès.](../install/media/python-379.png) 


#### <a name="install-pandas"></a>Installer pandas

Installez le package [pandas](https://pandas.pydata.org/) pour Python à partir d’une invite de commandes *élevée* :

```bash
python.exe -m pip install pandas
```

## <a name="update-the-system-environment-variables"></a>Mettez à jour les variables d'environnement système

Ajoutez ou modifiez PYTHONHOME en tant que variable d’environnement système.

+ Dans la zone de recherche Windows, tapez « environnement », puis sélectionnez **Modifier les variables d’environnement système**.
+ Sous l’onglet **Avancé**, sélectionnez **Variables d’environnement**.
+ Sous **Variables système**, sélectionnez **Nouveau** pour créer PYTHONHOME afin de pointer vers l’emplacement d’installation de Python 3.7.
Si PYTHONHOME existe déjà, sélectionnez **Modifier** pour le pointer vers l’emplacement d’installation Python 3.7.
+ Sélectionnez **OK** pour fermer les fenêtres restantes.

![Créez une variable système PYTHONHOME.](../install/media/sys-pythonhome.png)

## <a name="grant-access-to-the-custom-python-installation-folder"></a>Accordez l’accès au dossier d’installation de Python personnalisé

Exécutez les commandes **icacls** suivantes à partir d’une nouvelle invite de commandes *élevée* pour accorder l’accès READ & EXECUTE à PYTHONHOME au **Service SQL Server Launchpad** et SID **S-1-15-2-1** (**ALL APPLICATION PACKAGES**). Le nom d’utilisateur du service Launchpad est : `NT Service\MSSQLLAUNCHPAD$INSTANCENAME* where INSTANCENAME` est le nom de l’instance de votre serveur SQL Server. Les commandes accordent l’accès de manière récursive à tous les fichiers et dossiers sous le chemin d’un répertoire donné.

Ajoutez le nom de l’instance à `MSSQLLAUNCHPAD` (`MSSQLLAUNCHPAD$INSTANCENAME`). Dans cet exemple, INSTANCENAME est l’instance par défaut `MSSQLSERVER`.

1. Accordez des autorisations pour le **nom d’utilisateur du service SQL Server Launchpad**.

    ```cmd
    icacls "%PYTHONHOME%" /grant "NT Service\MSSQLLAUNCHPAD$MSSQLSERVER":(OI)(CI)RX /T

2. Give permissions to **SID S-1-15-2-1**.
    ```cmd
    icacls "%PYTHONHOME%" /grant *S-1-15-2-1:(OI)(CI)RX /T

>[!NOTE]
>The preceding command grants permissions to the computer **SID S-1-15-2-1**, which is equivalent to ALL APPLICATION PACKAGES on an English version of Windows. Alternatively, you can use `icacls "%R_HOME%" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T` on an English version of Windows.

## Restart SQL Server Launchpad service

From an *elevated* command prompt, run the following commands. Replace "MSSQLSERVER" with the name of your SQL Server instance.

```CMD
net stop MSSQLLAUNCHPAD$MSSQLSERVER
net start MSSQLLAUNCHPAD$MSSQLSERVER
```

Vous pouvez également cliquer avec le bouton droit sur le service de SQL Server Launchpad dans l’application **Services** du système, puis cliquer sur la commande **Redémarrer**. Ou utilisez le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md) pour redémarrer le service.

## <a name="download-python-language-extension"></a>Télécharger l’extension pour langage Python

Téléchargez le [fichier zip contenant l’extension de langage Python pour Windows](https://github.com/microsoft/sql-server-language-extensions/releases). Il est recommandé d’utiliser la version de production. Optez pour la version de débogage en développement ou en test, car elle fournit des informations de journalisation détaillées permettant d’examiner les erreurs.

## <a name="register-external-language"></a>Inscrire le langage externe

Pour chaque base de données dans laquelle vous souhaitez utiliser des extensions de langage Python, vous devez inscrire l’extension de langage avec [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md). Utilisez [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) pour se connecter à SQL Server et exécutez la commande T-SQL suivante. Modifiez le chemin d’accès dans cette instruction pour refléter l’emplacement du fichier zip de l’extension de langage téléchargé (python-lang-extension.zip).

> [!NOTE]
> Python est un mot réservé. Utilisez un nom différent pour la langue externe, par exemple « myPython ».

```sql
CREATE EXTERNAL LANGUAGE [myPython]
FROM (CONTENT = N'/path/to/python-lang-extension.zip', FILE_NAME = 'pythonextension.dll');
GO
```

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

Vous pouvez installer SQL Server sur Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) et Ubuntu. Pour plus d’informations, consultez la [section Plateformes prises en charge dans Conseils d’installation pour SQL Server sur Linux](../../linux/sql-server-linux-setup.md).

> [!NOTE]
> Cet article explique comment installer un CLR personnalisé pour l’exécution de scripts Python sur Linux. Pour installer sur Windows, consultez [Installer un CLR personnalisé Python pour SQL Server sur Windows](custom-runtime-python.md?view=sql-server-ver15&preserve-view=true)

## <a name="pre-install-checklist"></a>Liste de contrôle avant l’installation

Avant d’installer un CLR personnalisé Python, installez les éléments suivants :

+ [SQL Server 2019 pour Linux (avec la mise à jour cumulative 3 ou version ultérieure)](../../linux/sql-server-linux-setup.md).
Lorsque vous installez SQL Server sur Linux, vous devez configurer un référentiel Microsoft. Pour plus d’informations, consultez [Configuration des référentiels](../../linux/sql-server-linux-change-repo.md) (configuring repositories)

  > [!NOTE]
  > Le CLR personnalisé Python requiert une mise à jour cumulative (CU) 3 ou version ultérieure pour SQL Server 2019.

+ [Extensions de langage SQL Server sur Linux avec l’infrastructure d’extensibilité](../../linux/sql-server-linux-setup-language-extensions-java.md).

+ [Python 3.7](https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-linux"></a>Ajouter des Extensions de langage SQL Server pour Linux

> [!NOTE]
> Si vous avez Machine Learning Services installé sur SQL Server 2019, le package **mssql-server-extensibility** pour les extensions de langage est déjà installée et vous pouvez ignorer cette étape.

Les extensions de langage utilisent l’infrastructure d’extensibilité pour exécuter du code externe. L’exécution du code est isolée des processus du moteur de base, mais entièrement intégrée à l’exécution des requêtes SQL Server.

Utilisez les commandes suivantes pour installer les extensions de langage, selon votre version de Linux.

### <a name="ubuntu"></a>Ubuntu
> [!TIP]
> Si possible, `update` pour actualiser les packages sur le système avant l’installation. Ubuntu n’a peut-être pas l’option de transport https apt. Pour l’installer, utilisez `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility
```

### <a name="red-hat"></a>Red Hat
```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility
```

### <a name="suse"></a>SUSE
```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility
```

## <a name="install-python-37-and-pandas"></a>Installez Python 3.7 et pandas

Installez Python 3,7, la bibliothèque libpython 3.7 et le package pandas. 

Voici des exemples de commandes pour Ubuntu :

```bash
# Install python3.7 and the corresponding library:
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.7 python3-pip libpython3.7

# Install pandas to /usr/lib:
sudo python3.7 -m pip install pandas -t /usr/lib/python3.7/dist-packages
```

## <a name="using-a-custom-installation-of-python-37"></a>Utilisation d’une installation personnalisée de Python 3.7

> [!NOTE]
> Si vous avez installé Python à l’emplacement par défaut de `/usr/lib/python3.7`, vous pouvez passer à [l’étape suivante](#download-python-linux).

Si vous avez créé votre propre version de Python 3,7, utilisez les commandes suivantes pour que SQL Server puisse trouver et charger votre installation personnalisée.

### <a name="update-the-environment-variables"></a>Mettez à jour les variables d’environnement

1. Modifiez le service mssql-launchpad pour ajouter la variable d’environnement PYTHONHOME au fichier `/etc/systemd/system/mssql-launchpadd.service.d/override.conf`

      ```bash
      sudo systemctl edit mssql-launchpadd
      ```

    + Insérez le texte suivant dans le fichier `/etc/systemd/system/mssql-launchpadd.service.d/override.conf` qui s’ouvre. Définissez la valeur de PYTHONHOME sur le chemin d’installation de Python personnalisé.

      ```vi
      [Service]
      Environment="PYTHONHOME=/path/to/installation/of/python3.7"
      ```

    + Enregistrez et fermez.

2. Assurez-vous que `libpython3.7m.so.1.0` peut être chargé.

    + Créez un fichier custom-python.conf dans `/etc/ld.so.conf.d`.

      ```bash
      sudo vi /etc/ld.so.conf.d/custom-python.conf
      ```

    + Dans le fichier qui s’ouvre, ajoutez le chemin d’accès à **libpython3.7m.so.1.0** de l’installation Python personnalisée.

      ```vi
      /path/to/installation/of/python3.7/lib
      ```

    + Enregistrez et fermez le nouveau fichier.

    + Exécutez `ldconfig` et vérifiez que `libpython3.7m.so.1.0` peut être chargé en exécutant la commande suivante et en vérifiant que toutes les bibliothèques dépendantes peuvent être trouvées.

      ```bash
      sudo ldconfig
      ldd /path/to/installation/of/python3.7/lib/libpython3.7m.so.1.0
      ```

### <a name="grant-access-to-the-custom-python-folder"></a>Accordez l’accès au dossier Python personnalisé

Définissez l’option `datadirectories` de la section extensibilité du fichier /var/opt/mssql/mssql.conf sur l’installation personnalisée de Python.

```bash
sudo /opt/mssql/bin/mssql-conf set extensibility.datadirectories /path/to/installation/of/python3.7
```

### <a name="restart-the-mssql-launchpadd-service"></a>Redémarrez le service mssql-launchpad

```bash
sudo systemctl restart mssql-launchpadd
```
## <a name="download-python-language-extension"></a><a name="download-python-linux"></a> Télécharger l’extension pour langage Python

Téléchargez le [fichier zip contenant l’extension de langage Python pour Linux](https://github.com/microsoft/sql-server-language-extensions/releases). Il est recommandé d’utiliser la version de production. Optez pour la version de débogage en développement ou en test, car elle fournit des informations de journalisation détaillées permettant d’examiner les erreurs.

## <a name="register-external-language"></a>Inscrire le langage externe

Pour chaque base de données dans laquelle vous souhaitez utiliser des extensions de langage Python, vous devez inscrire l’extension de langage avec [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md). Utilisez [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) pour se connecter à SQL Server et exécutez la commande T-SQL suivante. 
Modifiez le chemin d’accès dans cette instruction pour refléter l’emplacement du fichier zip de l’extension de langage téléchargé (python-lang-extension.zip).

> [!NOTE]
>Python est un mot réservé. Utilisez un nom différent pour la langue externe, par exemple « myPython ».

```sql
CREATE EXTERNAL LANGUAGE myPython 
FROM (CONTENT = N'/PATH/TO/python-lang-extension.zip', FILE_NAME = 'libPythonExtension.so.1.0');
GO
```

::: moniker-end

## <a name="enable-external-script-execution-in-sql-server"></a>Activer l’exécution de scripts externes dans SQL Server

Un script externe dans Python peut être exécuté à l’aide de la procédure stockée [sp_execute_external script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) exécuté sur SQL Server. 

Pour activer les scripts externes, exécutez les commandes SQL suivantes à l’aide de [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md), connecté à SQL Server.

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

## <a name="verify-language-extension-installation"></a>Vérifiez l’installation de l’extension de langage

Ce script SQL teste les fonctionnalités de l’extension de langage installée.

```sql
EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
import sys
print(sys.path)
print(sys.version)
print(sys.executable)'
```

## <a name="verify-parameters-and-datasets-of-different-data-types"></a>Vérifiez les paramètres et les jeux de données de différents types de données

Ce script teste différents types de données pour les paramètres et les jeux de données d’entrée/sortie.

```sql
DECLARE @sumVal int = 12;
DECLARE @charVal VARCHAR(30) = N'Hello'

EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
print(sumVal)
print(charVal)
sumVal = sumVal + 300
OutputDataSet = InputDataSet'
,@input_data_1 = N'SELECT 1, CAST(1.4 as real), ''Hi'', CAST(''1'' as bit)'
,@params = N'@sumVal int OUTPUT, @charVal VARCHAR(30)'
,@sumVal = @sumVal OUTPUT
,@charVal = @charVal
WITH RESULT SETS ((intCol int, doubleCol real, charCol char(2), logicalCol bit));

PRINT @sumVal
```

## <a name="next-steps"></a>Étapes suivantes

+ [Framework d’extensibilité dans SQL Server](../concepts/extensibility-framework.md)
+ [Vue d’ensemble des extensions de langage](../../language-extensions/language-extensions-overview.md)
