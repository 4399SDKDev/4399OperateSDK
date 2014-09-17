**sdk�ṩ�������������뷽ʽ**

1. ȫ�Զ������� �������������߼���������ʾ������sdk��ɡ�
2. �Զ������������ ��Ϸ�������õ�������Ϣ���Զ����������档

# 1. ȫ�Զ�����
����Ϸ���ñ��ӿ�ʱ��SDK������̨�Ƿ����°汾��Ϸ���ߣ�����У�����ʾ�������ݣ�����ʾ�û�������������Ϊ`��������`����̨���ύ�°���Ϸʱ�Զ�������ְ�������ʱ�û�ֻ������APK�ļ����¾ɰ汾�в���Ĳ��֡���ظ������ݺͰ汾�ύ���ˣ�����ϵ4399�����Ӫ�Խ���Ա��
```java
OperateCenter.getInstance().updateApk(MainActivity.this);
```
# 2. �Զ�����������
## 1.1 ��ȡ�汾������Ϣ
### �ӿ�
```java
OperateCenter.getInstance().checkUpdateApk
```
### ����
> * Context: Activity��������
> * OnCheckFinishedListener: �����Ƿ����°汾�Ļص�

`OnCheckFinishedListener`���������ڷ��������°汾����Ϣ��
```java
/**
 * ����°汾�󣬷��ص��°汾��Ϣ
 * @param checkResultInfo �°汾��Ϣ�Ķ��� �����������˷��ص�������Ϣ
 * @param newApkFilePath  ����°汾�Ѿ�������ϣ���ͬʱ�����°汾�ļ�·���� ���� ����null
 */
 public void onCheckResponse(ApkCheckResult checkResultInfo, String newApkFilePath);
```
`ApkCheckResult`��һ���°汾���������Ҫ���з�����
-`getCode` �������󷵻���
-`getNewApkInfo` �°汾��Ϣ����һ��`GameUpgradeInfo`����

## 1.2 ��ʾ�汾������Ϣ
1. �ж�`onCheckResponse`�ص����ص�`checkResultInfo.getCode()`�Ƿ�Ϊ�ɹ���
2. ����ɹ���`checkResultInfo.getNewApkInfo()`��ȡ�°汾��Ϣ��������ʾ�����������棻

���й��з�����
```
> * getUpdateMsg    ��ȡ������log��Ϣ
> * getVersion      ��ȡ�汾����
> * getPatchSize    ��ȡ������С
> * getGameSize     ��ȡ��Ϸ���Ĵ�С
> * checkHavePatch  �ж��Ƿ��������� true���������� false����ȫ������
> * isCompel        �ж��Ƿ�ǿ������
> * getDate         ��ȡ�°汾��������
```
## 1.3 ��������
### �ӿ�
```java
OperateCenter.getInstance().doUpdate
```
### �������
> * Context: Activity��������
> * OnUpdateListener: �������̵ļ��������������Ⱥ����������

����`OnUpdateListener`�������Ķ������£�
```java
 public interface OnUpdateListener
    {
	/**
	 *
	 * Description: �������
	 *
	 * @param success �Ƿ�ɹ�
	 * @param resultCode ����������
	 */
	public void onUpdateSuccess(File newApkFile);
	public void onUpdateFail(int resultCode);
	
	/**
	 * ����°汾�󣬷��ص��°汾��Ϣ
	 * @param checkResultInfo �°汾��Ϣ�Ķ��� �����������˷��ص�������Ϣ
	 */
	public void onUpdateStart();
	
	/**
	 * �������̣����ز�������ȫ���Ľ��ȣ�
	 * �������������ɶ�Ӧ�Ĳ������������ز�������sdk��æ���ϳɲ�����Ϊ�°��apk��
	 * 
	 * @param progress 	��ǰ�����صĴ�С
	 * @param max	      	�ļ����ܴ�С
	 */
	public void onUpdateProgress(long progress, long max);
	
    }
```