Создание pool:

ceph osd pool create kubernetes

rbd pool init kubernetes

Предоставление прав пользователю kubernetes для pool'а

ceph auth get-or-create client.kubernetes mon 'profile rbd' osd 'profile rbd pool=kubernetes' mgr 'profile rbd pool=kubernetes'

Получаем ключ для пользователя admin на одной из нод ceph

ceph auth get-key client.kubernetes

Монтирование на клиентских машинах:

apt install ceph-fuse

ceph-fuse -m 172.17.25.50:6789 /mnt/cephfs --id admin  -d --no-mon-config
