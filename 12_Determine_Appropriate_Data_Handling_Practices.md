# **Data Leak Worksheet**

## **Incident summary**

A sales manager shared access to a folder of internal-only documents with their team during a meeting. The folder contained files associated with a new product that has not been publicly announced. It also included customer analytics and promotional materials. After the meeting, the manager did not revoke access to the internal folder, but warned the team to wait for approval before sharing the promotional materials with others.

During a video call with a business partner, a member of the sales team forgot the warning from their manager. The sales representative intended to share a link to the promotional materials so that the business partner could circulate the materials to their customers. However, the sales representative accidentally shared a link to the internal folder instead. Later, the business partner posted the link on their company's social media page assuming that it was the promotional materials.

---

## **Control:** Least privilege

## **Issue(s)**

Access to the internal folder was not limited to the sales team and the manager. The business partner should not have been given permission to share the promotional information to social media.

---

## **Review**

NIST SP 800-53: AC-6 addresses how an organization can protect their data privacy by implementing least privilege. It also suggests control enhancements to improve the effectiveness of least privilege.

---

## **Recommendation(s)**

* Restrict access to sensitive resources based on user role.
* Regularly audit user privileges.

---

## **Justification**

Data leaks can be prevented if shared links to internal files are restricted to employees only. Also, requiring managers and security teams to regularly audit access to team files would help limit the exposure of sensitive information.

---

## **Security plan snapshot**

| **Function** | **Category**         | **Subcategory**                         | **Reference(s)**     |
| ------------ | -------------------- | --------------------------------------- | -------------------- |
| Protect      | PR.DS: Data security | PR.DS-5: Protections against data leaks | NIST SP 800-53: AC-6 |

The implemented controls used by the organization to protect against data leaks are defined in **NIST SP 800-53**, which provides guidelines for securing the privacy of information systems.

---

## **NIST SP 800-53: AC-6 (Least Privilege)**

**Control:**
Only the minimal access and authorization required to complete a task or function should be provided to users.

**Discussion:**
Processes, user accounts, and roles should be enforced as necessary to achieve least privilege. The goal is to prevent a user from operating at privilege levels higher than what is necessary to accomplish business objectives.

**Control enhancements:**

* Restrict access to sensitive resources based on user role.
* Automatically revoke access to information after a period of time.
* Keep activity logs of provisioned user accounts.
* Regularly audit user privileges.

