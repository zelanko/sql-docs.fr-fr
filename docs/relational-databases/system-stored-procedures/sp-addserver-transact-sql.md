---
title: sp_addserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab5c15d15c77688c06eedec1d54e82c7b8199380
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492927"
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit le nom de l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque l’ordinateur qui héberge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est renommé, utilisez **sp_addserver** pour informer l’instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] du nouveau nom d’ordinateur. Cette procédure doit être exécutée sur toutes les instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] moteur de base de données hébergé sur l'ordinateur. Le nom de l'instance du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas être modifié. Pour modifier le nom d'une instance nommée, installez une nouvelle instance portant le nom souhaité, détachez les fichiers de base de données de l'ancienne instance, attachez les bases de données à la nouvelle instance, puis supprimez l'ancienne instance. Vous pouvez également créer un nom d'alias client sur l'ordinateur client, en redirigeant la connexion vers un autre nom de serveur et d'instance ou la combinaison **serveur:port** sans modifier le nom de l'instance sur l'ordinateur serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @server = ] 'server'` Est le nom du serveur. Les noms de serveurs doivent être uniques et suivre les règles de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows concernant les noms des ordinateurs, bien que l'utilisation d'espaces ne soit pas autorisée. *server* est de type **sysname**et n'a pas de valeur par défaut.  
  
 Lorsque plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées sur un ordinateur, chacune fonctionne comme si elle était sur un serveur distinct. Spécifiez une instance nommée en faisant référence à *server* comme *servername\instancename*.  
  
`[ @local = ] 'LOCAL'` Spécifie que le serveur est ajouté comme un serveur local. **@local** est **varchar (10)**, avec NULL comme valeur par défaut. Spécification **@local** comme **LOCAL** définit **@server** en tant que le nom du serveur local et @ le @@SERVERNAME fonction pour retourner la valeur de *server*.  
  
 Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte à cette variable le nom de l'ordinateur. Par défaut, le nom de l'ordinateur est la manière dont les utilisateurs se connectent à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans configuration complémentaire.  
  
 La définition locale entre uniquement en vigueur une fois le moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarré. Un seul serveur local peut être défini dans chaque instance du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ @duplicate_ok = ] 'duplicate_OK'` Spécifie si un nom de serveur en double est autorisé. **@duplicate_OK** est **varchar(13)**, avec NULL comme valeur par défaut. **@duplicate_OK** peut uniquement avoir la valeur **duplicate_OK** ou NULL. Si **duplicate_OK** est spécifié et le nom du serveur qui est déjà ajouté existe, aucune erreur n’est générée. Si les paramètres nommés ne sont pas utilisés, **@local** doit être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Pour définir ou désactivez les options de serveur, utilisez **sp_serveroption**.  
  
 **sp_addserver** ne peut pas être utilisé à l’intérieur d’une transaction définie par l’utilisateur.  
  
 À l’aide de **sp_addserver** pour ajouter un serveur distant n’est plus disponible. Utilisez de préférence [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **setupadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant remplace [!INCLUDE[ssDE](../../includes/ssde-md.md)] l'entrée du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le nom de l'ordinateur qui héberge  par `ACCOUNTS`.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Renommer un ordinateur qui héberge une Instance autonome de SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
