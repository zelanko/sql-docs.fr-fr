---
title: Instances d’utilisateur SQL Server Express
description: Décrit la prise en charge des instances utilisateur SQL Server Express.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 646eb9359dc5e7dfaad77bc3746fbfdf9ed9ce7a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920366"
---
# <a name="sql-server-express-user-instances"></a>Instances d’utilisateur SQL Server Express

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server Express Edition (SQL Server Express) prend en charge la fonctionnalité d'instance utilisateur, disponible uniquement avec le fournisseur de données Microsoft SqlClient Framework pour SQL Server. Une instance utilisateur est une instance distincte du moteur de base de données SQL Server Express générée par une instance parente. Les instances utilisateur permettent aux utilisateurs qui ne sont pas des administrateurs sur leurs ordinateurs locaux de joindre et de se connecter à des bases de données SQL Server Express. Chaque instance s’exécute dans le contexte de sécurité de l’utilisateur individuel, sur la base d’une instance par utilisateur.  
  
## <a name="user-instance-capabilities"></a>Fonctionnalités d’instance utilisateur  
Les instances utilisateur sont utiles pour les utilisateurs qui exécutent Windows dans le cadre d’un compte d’utilisateur disposant de privilèges minimum (LUA), car chaque utilisateur a des privilèges d'administrateur système SQL Server (`sysadmin`) sur l’instance en cours d’exécution sur son ordinateur sans avoir à l’exécuter en tant qu’administrateur Windows. Les logiciels qui s’exécutent sur une instance utilisateur avec des autorisations limitées ne peuvent pas apporter de modifications à l’ensemble du système, car l’instance SQL Server Express s’exécute sous le compte Windows non administrateur de l’utilisateur, pas en tant que service. Chaque instance utilisateur est isolée de l’instance parente et de toutes les autres instances utilisateur exécutées sur le même ordinateur. Les bases de données qui s’exécutent sur une instance utilisateur sont ouvertes uniquement en mode mono-utilisateur, et il n’est pas possible pour plusieurs utilisateurs de se connecter aux bases de données qui s’exécutent sur une instance utilisateur. La réplication et les requêtes distribuées sont également désactivées pour les instances utilisateur.  
  
Pour plus d’informations, Consultez « Instances utilisateur » dans la Documentation en ligne de SQL Server.  
  
> [!NOTE]
>  Les instances utilisateur ne sont pas nécessaires pour les utilisateurs qui sont déjà administrateurs sur leurs propres ordinateurs ou pour les scénarios impliquant plusieurs utilisateurs de base de données.  
  
## <a name="enabling-user-instances"></a>Activation des instances utilisateur  
Pour générer des instances d’utilisateur, une instance parente de SQL Server Express doit être en cours d’exécution. Les instances utilisateur sont activées par défaut lors de l’installation de SQL Server Express, et elles peuvent être activées ou désactivées de manière explicite par un administrateur système qui exécute la procédure stockée **système sp_configure** sur l’instance parente.  
  
```sql
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
Le protocole réseau pour les instances utilisateur doit être un canal nommé local. Une instance utilisateur ne peut pas être démarrée sur une instance distante de SQL Server, et les connexions SQL Server ne sont pas autorisées.  
  
## <a name="connecting-to-a-user-instance"></a>Connexion à une instance utilisateur  
Les mots clés `User Instance` et `AttachDBFilename`<xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A> autorisent <xref:Microsoft.Data.SqlClient.SqlConnection> à se connecter à une instance utilisateur. Les instances utilisateur sont également prises en charge par les propriétés <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>`UserInstance` et `AttachDBFilename`.  
  
Notez les points suivants à propos de l’exemple de chaîne de connexion présenté ci-dessous :  
  
- Le mot clé `Data Source` fait référence à l’instance parente de SQL Server Express qui génère l’instance utilisateur. L'instance par défaut est .\sqlexpress.  
  
- `Integrated Security` est défini sur `true`. Pour se connecter à une instance utilisateur, l’authentification Windows est requise ; les connexions SQL Server ne sont pas prises en charge.  
  
- La valeur `User Instance` est définie sur `true`, ce qui appelle une instance utilisateur. (La valeur par défaut est `false`.)  
  
- Le mot clé de chaîne de connexion `AttachDbFileName` est utilisé pour attacher le fichier de base de données primaire (.mdf), qui doit inclure le nom du chemin d’accès complet. `AttachDbFileName` correspond également aux clés « extended properties » et « initial file name » dans une chaîne de connexion <xref:Microsoft.Data.SqlClient.SqlConnection>.  
  
- La chaîne de substitution `|DataDirectory|` placée entre les symboles de barre verticale fait référence au répertoire de données de l’application qui ouvre la connexion et fournit un chemin d’accès relatif indiquant l’emplacement des fichiers journaux et de base de données .mdf et .ldf. Si vous souhaitez localiser ces fichiers ailleurs, vous devez fournir le chemin d’accès complet aux fichiers.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Vous pouvez également utiliser les propriétés <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder><xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> et <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> pour générer une chaîne de connexion au moment de l’exécution.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Utilisation de la chaîne de substitution &#124;DataDirectory&#124;  
`DataDirectory` est utilisé conjointement à `AttachDbFileName` pour indiquer un chemin relatif à un fichier de données, ce qui permet aux développeurs de créer des chaînes de connexion basées sur un chemin relatif à la source de données au lieu de devoir spécifier un chemin complet.  
  
L’emplacement physique vers lequel `DataDirectory` pointe dépend du type d’application. Dans cet exemple, le fichier Northwind.mdf à joindre se trouve dans le dossier \app_data de l’application.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
Lorsque `DataDirectory` est utilisé, le chemin de fichier résultant ne peut pas être plus haut dans la structure de répertoires que le répertoire vers lequel pointe la chaîne de substitution. Par exemple, si le `DataDirectory` entièrement développé est C:\AppDirectory\app_data, l’exemple de chaîne de connexion illustré ci-dessus fonctionne, car il est situé sous C:\AppDirectory. Cependant, si vous tentez de spécifier `DataDirectory` sous la forme `|DataDirectory|\..\data`, il en résulte une erreur car \data n’est pas un sous-répertoire de \AppDirectory.  
  
Si la chaîne de connexion a une chaîne de substitution mal mise en forme, une <xref:System.ArgumentException> est levée.  
  
> [!NOTE]
>  <xref:Microsoft.Data.SqlClient> résout les chaînes de substitution en chemins d’accès complets sur le système de fichiers de l’ordinateur local. Par conséquent, les noms de chemin d’accès de serveur distant, HTTP et UNC ne sont pas pris en charge. Une exception est levée lorsque la connexion est ouverte si le serveur ne se trouve pas sur l’ordinateur local.  
  
Quand la <xref:Microsoft.Data.SqlClient.SqlConnection> est ouverte, elle est redirigée de l’instance SQL Server Express par défaut vers une instance initiée au moment de l’exécution, qui s’exécute sous le compte de l’appelant.  
  
> [!NOTE]
>  Il peut être nécessaire d’augmenter la valeur de <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionTimeout%2A>, car le chargement des instances utilisateur peut prendre plus de temps que les instances normales.  
  
Le fragment de code suivant ouvre une nouvelle `SqlConnection`, affiche la chaîne de connexion dans la fenêtre de console, puis ferme la connexion lors de la sortie du bloc de code `using`.  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
>  Les instances utilisateur ne sont pas prises en charge dans le Common Language Runtime (CLR) qui s’exécute dans SQL Server. Une <xref:System.InvalidOperationException> est levée si `Open` est appelé sur une <xref:Microsoft.Data.SqlClient.SqlConnection> qui a `User Instance=true` dans la chaîne de connexion.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Durée de vie d’une connexion d’instance utilisateur  
Contrairement aux versions de SQL Server qui s’exécutent en tant que service, les instances SQL Server Express n’ont pas besoin d’être démarrées et arrêtées manuellement. Chaque fois qu’un utilisateur s’identifie et se connecte à une instance utilisateur, l’instance utilisateur est démarrée si elle n’est pas déjà en cours d’exécution. L’option `AutoClose` est définie pour les bases de données d’instance utilisateur afin que la base de données s’arrête automatiquement après une période d’inactivité. Le processus sqlservr.exe démarré reste en cours d’exécution pendant un délai d’attente limité après la fermeture de la dernière connexion à l’instance ; il n’est donc pas nécessaire de redémarrer si une autre connexion est ouverte avant l’expiration du délai d’attente. L’instance utilisateur s’arrête automatiquement si aucune nouvelle connexion n’est ouverte avant l’expiration du délai d’attente. Un administrateur système sur l’instance parente peut définir la durée du délai d’attente pour une instance utilisateur à l’aide de **sp_configure** afin de modifier l’option de **délai d’attente de l’instance utilisateur**. La valeur par défaut est de 60 minutes.  
  
> [!NOTE]
>  Si `Min Pool Size` est utilisé dans la chaîne de connexion avec une valeur supérieure à zéro, le dispositif de regroupement garde toujours quelques connexions ouvertes et l’instance utilisateur ne s’arrête pas automatiquement.  
  
## <a name="how-user-instances-work"></a>Fonctionnement des instances utilisateur  
La première fois qu’une instance utilisateur est générée pour chaque utilisateur, les bases de données système **master** et **msdb** sont copiées du dossier Template Data vers un chemin sous le répertoire de stockage des données d’application local de l’utilisateur pour être utilisées exclusivement par l’instance utilisateur. Ce chemin d’accès est généralement `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Quand une instance utilisateur démarre, les fichiers **tempdb**, journaux et de suivi sont aussi écrits dans ce répertoire. Un nom est généré pour l’instance, et son unicité est garantie pour chaque utilisateur.  
  
Par défaut, tous les membres du groupe Windows Builtin\Users disposent des autorisations pour se connecter à l’instance locale, ainsi que des autorisations de lecture et d’exécution sur les fichiers binaires de SQL Server. Une fois que les informations d’identification de l’utilisateur appelant qui héberge l’instance utilisateur ont été vérifiées, cet utilisateur devient le `sysadmin` sur cette instance. Seule la mémoire partagée est activée pour les instances utilisateur, ce qui signifie que seules les opérations sur l’ordinateur local sont possibles.  
  
Les utilisateurs doivent disposer d’autorisations en lecture et en écriture sur les fichiers .mdf et .ldf spécifiés dans la chaîne de connexion.  
  
> [!NOTE]
>  Les fichiers .mdf et .ldf représentent les fichiers de base de données et les fichiers journaux, respectivement. Ces deux fichiers étant un ensemble mis en correspondance, il convient de faire preuve de prudence lors des opérations de sauvegarde et de restauration. Le fichier de base de données contient des informations sur la version exacte du fichier journal, et la base de données ne s’ouvre pas si elle est couplée au mauvais fichier journal.  
  
Pour éviter tout endommagement des données, une base de données de l’instance utilisateur est ouverte avec un accès exclusif. Si deux instances utilisateur différentes partagent la même base de données sur le même ordinateur, l’utilisateur sur la première instance doit fermer la base de données avant de pouvoir l’ouvrir dans une deuxième instance.  
  
## <a name="user-instance-scenarios"></a>Scénarios d’instance utilisateur  
Les instances utilisateur fournissent aux développeurs d’applications de base de données un magasin de données SQL Server qui ne nécessite pas que les développeurs disposent de comptes d’administration sur leurs ordinateurs de développement. Les instances utilisateur sont basées sur le modèle Access/Jet, où l’application de base de données se connecte simplement à un fichier, et l’utilisateur dispose automatiquement d’autorisations complètes sur tous les objets de base de données sans avoir besoin de l’intervention d’un administrateur système pour accorder des autorisations. Ce comportement est prévu pour fonctionner dans des situations où l’utilisateur s’exécute sous un compte d’utilisateur avec des privilèges minimum et ne dispose pas de privilèges d’administrateur sur le serveur ou l’ordinateur local, mais a besoin de créer des objets et applications de base de données. Les instances utilisateur permettent aux utilisateurs de créer des instances au moment de l’exécution qui s’exécutent sous le contexte de sécurité de l’utilisateur, et non dans le contexte de sécurité d’un service système plus privilégié.  
  
> [!IMPORTANT]
>  Les instances utilisateur ne doivent être utilisées que dans les scénarios où toutes les applications qui l’utilisent sont entièrement fiables.  
  
Les scénarios d’instance utilisateur sont les suivants :  
  
- Toute application mono-utilisateur où le partage de données n’est pas requis.  
  
- Déploiement ClickOnce. Si .NET Framework 2.0 (ou version ultérieure) ou .NET Core 1.0 (ou version ultérieure) et SQL Server Express sont déjà installés sur l’ordinateur cible, le package d’installation téléchargé suite à une action ClickOnce peut être installé et utilisé par des utilisateurs qui ne sont pas administrateurs. Notez qu’un administrateur doit installer SQL Server Express s’il fait partie de l’installation. Pour plus d'informations, consultez [Déploiement ClickOnce pour Windows Forms](https://docs.microsoft.com/dotnet/framework/winforms/clickonce-deployment-for-windows-forms).
  
- Hébergement ASP.NET dédié à l’aide de l’authentification Windows. Une seule instance SQL Server Express peut être hébergée sur un intranet. L’application se connecte à l’aide du compte Windows ASPNET, et non à l’aide de l’emprunt d’identité. Les instances utilisateur ne doivent pas être utilisées pour les scénarios d’hébergement tiers ou partagé, où toutes les applications partagent la même instance utilisateur et ne sont plus isolées les unes des autres.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
