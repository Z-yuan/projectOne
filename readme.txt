����û���
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

��ʾ��ǰĿ¼pwd
�����Ŀ¼���Git���Թ���Ĳֿ⣺git init

��һ����������git add����Git�����ļ���ӵ��ֿ⣺
git add text.txt

�ڶ�����������git commit����Git�����ļ��ύ���ֿ⣺
git commit 
�򵥽���һ��git commit���-m����������Ǳ����ύ��˵��
git commit -m "��θĶ���˵��"

git status�������������ʱ�����ղֿ⵱ǰ��״̬
git status

git diff�鿴�޸�����
git diff

git log������Ը��������ύ����ʷ��¼
git log
����������Ϣ̫�࣬�����ۻ����ҵģ��������Լ���--pretty=oneline������
$ git log --pretty=oneline

��Git�У���HEAD��ʾ��ǰ�汾����һ���汾����HEAD^������һ���汾����HEAD^^����Ȼ����100���汾д100��^�Ƚ�������������������д��HEAD~100��
git reset������Ի��˰汾
$ git reset --hard HEAD^������ǻ��˵���һ�汾��
����������´�ӡgit log�Ϳ��������µ��ύ��ʷ�ˣ�����뷵��ȥ��Ҫ��û��Git��ʱ���ҵ����µ�commit ID�ţ����磨commit 6146ec8c7d5a8156a11c7af2ca7650828faf15a3��������ȫ�����룬����ǰ��λ���Ϳ���
git reset --hard 6146ec

�ֶ����ļ��ָ�����һ���汾��״̬��git checkout -- file���Զ������������޸ģ�
git checkout -- readme.txt
����git checkout -- readme.txt��˼���ǣ���readme.txt�ļ��ڹ��������޸�ȫ�����������������������
һ����readme.txt���޸ĺ�û�б��ŵ��ݴ��������ڣ������޸ľͻص��Ͱ汾��һģһ����״̬��
һ����readme.txt�Ѿ���ӵ��ݴ������������޸ģ����ڣ������޸ľͻص���ӵ��ݴ������״̬��
��֮������������ļ��ص����һ��git commit��git addʱ��״̬��

�����Ҫ�ǰ�����ļ�git add�ύ���ݴ����˾�Ҫ������git reset HEAD <file>���԰��ݴ������޸ĳ�������unstage�������·Żع�������
git reset HEAD readme.txt
������ύ���汾����Ի��˵���һ���汾���������������������ģ������㻹û�а��Լ��ı��ذ汾�����͵�Զ�̡����ǵ�Git�Ƿֲ�ʽ�汾����ϵͳ�����Ǻ���ὲ��Զ�̰汾�⣬һ�����stupid boss�ύ���͵�Զ�̰汾�⣬�����Ĳ��ˡ���

һ������£���ͨ��ֱ�����ļ��������а�û�õ��ļ�ɾ�ˣ�������rm����ɾ�ˣ�
rm test.txt
���ʱ��Git֪����ɾ�����ļ�����ˣ��������Ͱ汾��Ͳ�һ���ˣ�git status��������̸�������Щ�ļ���ɾ���ˣ�
������������ѡ��һ��ȷʵҪ�Ӱ汾����ɾ�����ļ����Ǿ�������git rmɾ��������git commit��
git rm test.txt
git commit -m "remove test.txt"
��һ�������ɾ���ˣ���Ϊ�汾���ﻹ���أ����Կ��Ժ����ɵذ���ɾ���ļ��ָ������°汾��
git checkout -- test.txt
git checkout��ʵ���ð汾����İ汾�滻�������İ汾�����۹��������޸Ļ���ɾ���������ԡ�һ����ԭ����

����Զ�ֿ̲�
��1��������SSH Key�����û���Ŀ¼�£�������û��.sshĿ¼������У��ٿ������Ŀ¼����û��id_rsa��id_rsa.pub�������ļ�������Ѿ����ˣ���ֱ��������һ�������û�У���Shell��Windows�´�Git Bash��������SSH Key��
ssh-keygen -t rsa -C "1171326259@qq.com"
����Ҫ���ʼ���ַ�������Լ����ʼ���ַ��Ȼ��һ·�س���ʹ��Ĭ��ֵ���ɣ��������KeyҲ�������ھ���Ŀ�ģ�����Ҳ�����������롣
���һ��˳���Ļ����������û���Ŀ¼���ҵ�.sshĿ¼��������id_rsa��id_rsa.pub�����ļ�������������SSH Key����Կ�ԣ�id_rsa��˽Կ������й¶��ȥ��id_rsa.pub�ǹ�Կ�����Է��ĵظ����κ��ˡ�
��2������½GitHub���򿪡�Account settings������SSH Keys��ҳ�棺Ȼ�󣬵㡰Add SSH Key������������Title����Key�ı�����ճ��id_rsa.pub�ļ������ݣ�
ΪʲôGitHub��ҪSSH Key�أ���ΪGitHub��Ҫʶ��������͵��ύȷʵ�������͵ģ������Ǳ���ð��ģ���Git֧��SSHЭ�飬���ԣ�GitHubֻҪ֪������Ĺ�Կ���Ϳ���ȷ��ֻ�����Լ��������͡�
���������ʾ����GitHub������йܵ�Git�ֿ⣬�κ��˶����Կ���ร���ֻ�����Լ����ܸģ������ԣ���Ҫ��������Ϣ�Ž�ȥ��

���Զ�̿�
���ڵ��龰�ǣ����Ѿ��ڱ��ش�����һ��Git�ֿ��������GitHub����һ��Git�ֿ⣬�������������ֿ����Զ��ͬ����������GitHub�ϵĲֿ�ȿ�����Ϊ���ݣ��ֿ�����������ͨ���òֿ���Э��������һ�ٶ�á�
���ȣ���½GitHub��Ȼ�������Ͻ��ҵ���Create a new repo����ť������һ���µĲֿ⣺
��Repository name����XXXXXXXX����������Ĭ�����ã������Create repository����ť���ͳɹ��ش�����һ���µ�Git�ֿ⣺
Ŀǰ����GitHub�ϵ����XXXXXX�ֿ⻹�ǿյģ�GitHub�������ǣ����Դ�����ֿ��¡���µĲֿ⣬Ҳ���԰�һ�����еı��زֿ���֮������Ȼ�󣬰ѱ��زֿ���������͵�GitHub�ֿ⡣
���ڣ����Ǹ���GitHub����ʾ���ڱ��ص�XXXXXX�ֿ����������
git remote add origin git@github.com:Z-yuan���˻�����/XXXXX���ֿ�����.git
�ѱ��ؿ���������͵�Զ�̣���git push���ʵ�����ǰѵ�ǰ��֧master���͵�Զ�̡�
git push -u origin master
����Զ�̿��ǿյģ����ǵ�һ������master��֧ʱ��������-u������Git������ѱ��ص�master��֧�������͵�Զ���µ�master��֧������ѱ��ص�master��֧��Զ�̵�master��֧�������������Ժ�����ͻ�����ȡʱ�Ϳ��Լ����
��������ֻҪ���������ύ���Ϳ���ͨ�����
git push origin master
SSH����
�����һ��ʹ��Git��clone����push��������GitHubʱ����õ�һ�����棺
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
������ΪGitʹ��SSH���ӣ���SSH�����ڵ�һ����֤GitHub��������Keyʱ����Ҫ��ȷ��GitHub��Key��ָ����Ϣ�Ƿ��������GitHub�ķ�����������yes�س����ɡ�

������ϲ���֧