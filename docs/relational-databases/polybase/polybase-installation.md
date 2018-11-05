---
title: Installer PolyBase sur Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase, installation
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e30cded830401c589c62d1e6301d5be78720c07f
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806749"
---
# <a name="install-polybase-on-windows"></a>Installer PolyBase sur Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Pour installer une version d'évaluation de SQL Server, accédez à [Versions d’évaluation de SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016). 
   
## <a name="prerequisites"></a>Conditions préalables requises  
   
- Version d’évaluation de SQL Server 64 bits  
   
- Microsoft .NET Framework 4.5  

- Oracle Java SE Runtime Environment (JRE). Les versions 7 (à partir de la version 7.51) et 8 sont prises en charge ([JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) et [Server JRE](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) fonctionnent). Accédez à [Java SE downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)(Téléchargements Java SE). Le programme d’installation échoue si JRE n’est pas présent. JRE9 et JRE10 ne sont pas pris en charge.

- Mémoire minimale : 4 Go  
   
- Espace libre minimal sur le disque dur : 2 Go  
- **Recommandé :** 16 Go de RAM au minimum
   
- TCP/IP doit être activé pour que PolyBase fonctionne correctement. TCP/IP est activé par défaut sur toutes les éditions de SQL Server, sauf sur les éditions SQL Server Express et Developer. Pour que PolyBase fonctionne correctement sur les éditions Express et Developer, vous devez activer la connectivité TCP/IP (consultez [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).)

- MSVC++ 2012 

**Remarque**  

Il n'est possible d'installer PolyBase que sur une instance SQL Server par ordinateur.

> **Important**
>
> Si vous envisagez d’utiliser la fonctionnalité de calcul pushdown sur Hadoop, vérifiez que le cluster Hadoop cible est bien doté des principaux composants HDFS et Yarn/MapReduce, avec le serveur Jobhistory activé. PolyBase envoie la requête émise via MapReduce et extrait l’état à partir du serveur JobHistory. L’absence de l’un ou l’autre des composants entraîne l’échec de la requête.
  
## <a name="single-node-or-polybase-scaleout-group"></a>Nœud unique ou groupe PolyBase avec montée en puissance parallèle

Avant de commencer l’installation de PolyBase sur vos instances SQL Server, décidez si l’installation doit être faite sur un nœud unique ou dans un [groupe de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).

Pour un groupe de scale-out PolyBase, vous devez veiller à ce que :

- Toutes les machines figurent dans le même domaine.
- Vous utilisez les mêmes compte de service et mot de passe pendant l’installation de PolyBase.
- Vos instances de SQL Server peuvent communiquer entre elles sur le réseau.
- Les instances de SQL Server sont toutes la même version de SQL Server.

Une fois que vous avez installé PolyBase de façon autonome ou dans un groupe de scale-out, vous ne pouvez plus modifier ce réglage. Vous devez désinstaller et réinstaller la fonctionnalité pour modifier ce paramètre.

## <a name="install-using-the-installation-wizard"></a>Installation avec l’assistant Installation  
   
1. Exécutez le fichier setup.exe de SQL Server.   
   
2. Cliquez sur **Installation**, puis sur **Nouvelle installation autonome de SQL Server, ou ajouter des fonctionnalités**.  
   
3. Sur la page de sélection de fonctionnalités, sélectionnez **Service de requête PolyBase pour données externes**.  

 ![Services PolyBase](../../relational-databases/polybase/media/install-wizard.png "Services PolyBase")  
   
4. Dans la page de configuration du serveur, configurez le **Service de moteur SQL Server PolyBase** et le service Mouvement de données PolyBase SQL Server à exécuter sous le même compte de domaine.  
   
 > **IMPORTANT !** 
>
>Dans un groupe de scale-out PolyBase, le moteur PolyBase et le service de déplacement PolyBase doivent être exécutés sous le même compte de domaine, et ce sur tous les nœuds. Voir [Groupes de scale-out PolyBase](#Enable)
   
5. Sur la **Page de configuration de PolyBase**, sélectionnez une des deux options. Pour plus d’informations, consultez [Groupes de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md) .  
   
   - Utilisez l’instance de SQL Server comme instance activée PolyBase autonome.  
   
     Choisissez cette option pour utiliser cette instance SQL Server comme nœud principal autonome.  
   
   - Utilisez l’instance de SQL Server dans le cadre du groupe de scale-out PolyBase.  Le choix de cette option ouvre le pare-feu pour autoriser les connexions entrantes au moteur de base de données SQL Server, au moteur PolyBase SQL Server, au service Mouvement de données PolyBase SQL Server et à SQL Browser. Le pare-feu est ouvert pour autoriser les connexions entrantes à partir d'autres nœuds dans un groupe de scale-out PolyBase.  
   
     Le choix de cette option activera également les connexions du pare-feu Microsoft Distributed Transaction Coordinator (MSDTC) et modifiera les paramètres du registre MSDTC.  
   
6. Sur la **Page de configuration de PolyBase**, spécifiez une plage de ports avec au moins six ports. Le programme d'installation de SQL Server affectera les six premiers ports disponibles sur la plage.  

  > **IMPORTANT !**
  >
  > Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).


##  <a name="installing"></a> Installation avec une invite de commandes  

Utilisez les valeurs de cette table pour créer des scripts d'installation. Les deux services **Moteur SQL Server PolyBase** et **Service de déplacement de données SQL Server PolyBase** doivent s’exécuter sous le même compte. Dans un groupe de scale-out PolyBase, les services PolyBase doivent être exécutés sous le même compte de domaine, et ce sur tous les nœuds.  
   
<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017"

|composant SQL Server|Paramètre et valeurs|Description|  
|--------------------------|--------------------------|-----------------|  
|Contrôle d'installation de SQL Server|**Requis**<br /><br /> /FEATURES=PolyBase|Sélectionne la fonctionnalité PolyBase.|  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCACCOUNT|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCPASSWORD|Spécifie le mot de passe du compte de service du moteur.|  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCSTARTUPTYPE|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|Service de déplacement de données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCACCOUNT|Spécifie le compte pour le service de déplacement des données. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|Service de déplacement des données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCPASSWORD|Spécifie le mot de passe du compte de déplacement des données.|  
|Service de déplacement des données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCSTARTUPTYPE|Spécifie le mode de démarrage pour le service de déplacement des données : automatique (par défaut), désactivé ou manuel|  
|PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBSCALEOUT|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. <br />Valeurs prises en charge : **True**, **False**|  
|PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBPORTRANGE|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

|composant SQL Server|Paramètre et valeurs|Description|  
|--------------------------|--------------------------|-----------------|  
|Contrôle d'installation de SQL Server|**Obligatoire**<br /><br /> /FEATURES= PolyBaseCore, PolyBaseJava, PolyBase | **PolyBaseCore** installe la prise en charge de toutes les fonctionnalités de PolyBase, à l’exception de la connectivité Hadoop. **PolyBaseJava** active la connectivité Hadoop. **PolyBase** installe les deux. |  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCACCOUNT|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCPASSWORD|Spécifie le mot de passe du compte de service du moteur.|  
|Moteur SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBENGSVCSTARTUPTYPE|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|Service de déplacement de données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCACCOUNT|Spécifie le compte pour le service de déplacement des données. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|Service de déplacement des données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCPASSWORD|Spécifie le mot de passe du compte de déplacement des données.|  
|Service de déplacement des données SQL Server PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBDMSSVCSTARTUPTYPE|Spécifie le mode de démarrage pour le service de déplacement des données : automatique (par défaut), désactivé ou manuel|  
|PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBSCALEOUT|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. <br />Valeurs prises en charge : **True**, **False**|  
|PolyBase|**Ce paramètre est facultatif**<br /><br /> /PBPORTRANGE|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end

Après l’installation, vous devez [activer la fonctionnalité PolyBase](#enable).



**Exemple**

Voici un exemple de script d'installation.  

```cmd
   
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
   
```  

## <a id="enable"></a> Activer PolyBase

Une fois que vous avez terminé l’installation, PolyBase doit être activé pour accéder à ses fonctionnalités. Pour vous connecter à SQL Server 2019 CTP 2.0, vous devez activer PolyBase après l’installation à l’aide de la commande Transact-SQL suivante :


```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [ WITH OVERRIDE ]  ;
```
L’instance doit ensuite être **redémarrée**. 


## <a name="post-installation-notes"></a>Notes post-installation  

PolyBase installe trois bases de données utilisateur, DWConfiguration, DWDiagnostics et DWQueue.   Elles doivent être utilisées avec PolyBase et ne doivent pas être modifiées ni supprimées.  
   
### <a id="confirminstall"></a> Comment vérifier l’installation  

Exécutez la commande suivante : Si PolyBase est installé, renvoie la valeur 1, sinon 0.  

```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  

### <a name="firewall-rules"></a>Règles de pare-feu  

Le programme d'installation de SQL Server PolyBase crée les règles de pare-feu suivantes sur l'ordinateur.  
   
- SQL Server PolyBase – Moteur de base de données - \<NomInstanceSQLServer> (TCP-entrant)  
   
- SQL Server PolyBase – Services PolyBase - \<NomInstanceSQLServer> (TCP-entrant)  

- SQL Server PolyBase - SQL Browser - (UDP-entrant)  
   
Lors de l’installation, si vous choisissez d’utiliser l’instance SQL Server dans le cadre d’un groupe de scale-out PolyBase, ces règles sont activées et le pare-feu est ouvert pour autoriser les connexions entrantes au moteur de base de données de SQL Server, au moteur SQL Server PolyBase, au service Mouvement de données PolyBase SQL Server et à SQL Browser. Cependant, si le service de pare-feu de l’ordinateur n’est pas exécuté au moment de l’installation, la configuration de SQL Server ne pourra pas activer ces règles. Dans ce cas, vous devez démarrer le service de pare-feu sur l'ordinateur et activer ces règles après l'installation.  
   
#### <a name="to-enable-the-firewall-rules"></a>Pour activer les règles de pare-feu  

- Ouvrez le **Panneau de configuration**.  

- Cliquez sur **Système et sécurité**, puis sur **Pare-feu Windows**.  
   
- Cliquez sur **Paramètres avancés**, puis sur **Règles de trafic entrant**.  
   
- Cliquez avec le bouton droit sur la règle désactivée, puis cliquez sur **Activer la règle**.  
   
### <a name="polybase-service-accounts"></a>Comptes de service PolyBase

Pour modifier les comptes de service pour le moteur PolyBase et les services de déplacement de données PolyBase, désinstallez et réinstallez la fonctionnalité PolyBase.

## <a name="next-steps"></a>Étapes suivantes  

Consultez [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).
