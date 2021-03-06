    usage: jpg2dcm [options] <jpeg-file>|<mpeg2-file> <dicom-file>
    
    Encapsulate JPEG image or MPEG2 video (with file extensions jpeg, jpg,
    jpe; mpeg, mpg, mpe) into DICOM files. DICOM attributes can be specified
    via command line (using -a option) or a XML file (using -f option).
    -
    Options:
     -a <[seq/]attr=value>   specify included DICOM Attribute. attr can be
                             specified by keyword or tag value (in hex), e.g.
                             PatientName or00100010. Attributes in nested
                             Datasets can be specified by including the
                             keyword/tag value of the sequence attribute,e.g.
                             00400275/00400009 for Scheduled Procedure Step ID
                             in the Request Attributes Sequence. Overrides
                             DICOM attributesspecified by -f <xml-file>
     -f <xml-file>           specify included DICOM attributes by XML
                             presentation in <xml-file>
     -h,--help               display this help and exit
        --no-app             remove application segments APPn from
                             encapsulated JPEG stream; encapsulate JPEG stream
                             verbatim by default.
     -V,--version            output version information and exit
    -
    Example 1: jpg2dcm -f metadata.xml image.jpg image.dcm
    => Encapulate JPEG Image verbatim with DICOM attributes specified in
    metadata.xml into DICOM Image Object.
    -
    Example 2: jpg2dcm --no-app -a PatientName=Simson^Homer -a PatientSex=M
    homer.jpg image.dcm
    => Encapulate JPEG Image without application segments with specified DICOM
    attributes into DICOM Image Object.
    -
    Example 3: jpg2dcm video.mpg video.dcm
    => Encapulate MPEG2 Video into DICOM Video Object.
