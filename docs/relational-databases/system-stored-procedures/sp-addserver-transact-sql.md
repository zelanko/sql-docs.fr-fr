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
ms.openlocfilehash: 8924a2a5c0960137eb5fe2a78d2ea7f3521b3929
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72381715"
---
# <a name="sp_addserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit le nom de l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque l’ordinateur qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] héberge est renommé, utilisez **sp_addserver** pour informer l’instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] du nouveau nom d’ordinateur. Cette procédure doit être exécutée sur toutes les instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] moteur de base de données hébergé sur l'ordinateur. Le nom de l'instance du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas être modifié. Pour modifier le nom d'une instance nommée, installez une nouvelle instance portant le nom souhaité, détachez les fichiers de base de données de l'ancienne instance, attachez les bases de données à la nouvelle instance, puis supprimez l'ancienne instance. Vous pouvez également créer un nom d'alias client sur l'ordinateur client, en redirigeant la connexion vers un autre nom de serveur et d'instance ou la combinaison **serveur:port** sans modifier le nom de l'instance sur l'ordinateur serveur.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @server = ] 'server'`Nom du serveur. Les noms de serveurs doivent être uniques et suivre les règles de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows concernant les noms des ordinateurs, bien que l'utilisation d'espaces ne soit pas autorisée. *Server* est de **type sysname**, sans valeur par défaut.  
  
 Lorsque plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées sur un ordinateur, chacune fonctionne comme si elle était sur un serveur distinct. Spécifiez une instance nommée en faisant référence au *serveur* en tant que *NomServeur\NomInstance*.  
  
`[ @local = ] 'LOCAL'`Spécifie que le serveur est ajouté en tant que serveur local. local est de type **varchar (10)**, avec NULL comme valeur par défaut. ** \@** Si vous spécifiez ** \@local** As **local** , le ** \@serveur** est défini comme le nom du serveur@SERVERNAME local et la fonction @ retourne la valeur de *Server*.  
  
 Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte à cette variable le nom de l'ordinateur. Par défaut, le nom de l'ordinateur est la manière dont les utilisateurs se connectent à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans configuration complémentaire.  
  
 La définition locale entre uniquement en vigueur une fois le moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarré. Un seul serveur local peut être défini dans chaque instance du moteur de base de données [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ @duplicate_ok = ] 'duplicate_OK'`Spécifie si un nom de serveur en double est autorisé. duplicate_OK est de type **varchar (13)**, avec NULL comme valeur par défaut. ** \@** duplicate_OK peut uniquement avoir la valeur **duplicate_OK** ou null. ** \@** Si **duplicate_OK** est spécifié et que le nom du serveur en cours d’ajout existe déjà, aucune erreur n’est générée. Si les paramètres nommés ne sont pas utilisés, ** \@local** doit être spécifié.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Pour définir ou supprimer des options de serveur, utilisez **sp_serveroption**.  
  
 **sp_addserver** ne peut pas être utilisé dans une transaction définie par l’utilisateur.  
  
 L’utilisation de **sp_addserver** pour ajouter un serveur distant n’est plus disponible. Utilisez à la place [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **setupadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant remplace [!INCLUDE[ssDE](../../includes/ssde-md.md)] l'entrée du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le nom de l'ordinateur qui héberge  par `ACCOUNTS`.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Renommer un ordinateur qui héberge une instance autonome de SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
