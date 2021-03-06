#
# Rule engine lib build
#
ADD_LIBRARY(ruleengine
	backwardchainer/BackwardChainer
	backwardchainer/BackwardChainerPMCB
	backwardchainer/BIT
	backwardchainer/UnifyPMCB
	backwardchainer/BCLogger
	forwardchainer/FCStat
	forwardchainer/FocusSetPMCB
	forwardchainer/ForwardChainer
	forwardchainer/VarGroundingPMCB
	forwardchainer/FCLogger
	ChainerUtils.cc
	InferenceSCM.cc
	Rule.cc
	URECommons.cc
	UREConfigReader.cc
)

ADD_DEPENDENCIES(ruleengine
	opencog_atom_types
)

TARGET_LINK_LIBRARIES(ruleengine
	lambda
	query
	smob
	execution
	atomutils
	atomspace
	atomspaceutils
)

INSTALL (TARGETS ruleengine DESTINATION "lib${LIB_DIR_SUFFIX}/opencog")

INSTALL (FILES
	UREConfigReader.h
	URECommons.h
	Rule.h
	UREConfigReader.h
	DESTINATION "include/opencog/rule-engine"
)

ADD_SUBDIRECTORY(forwardchainer)
ADD_SUBDIRECTORY(backwardchainer)
